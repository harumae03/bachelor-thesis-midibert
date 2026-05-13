# Helilooja tuvastamine ja tähelepanumehhanismi visualiseerimine MidiBERTi mudeli abil

Bakalaureusetöö (Tartu Ülikool, arvutiteaduse instituut, 2026)

Autor: Hannes Arumäe
Juhendaja: Anna Aljanaki, PhD

## Kirjeldus

Töös peenhäälestatakse MidiBERT-Piano mudel helilooja tuvastamiseks ning analüüsitakse mudeli otsustusprotsessi kumulatiivse tähelepanu (attention rollout) meetodiga.

## Failid

| Fail | Kirjeldus |
|------|-----------|
| `Atepp_parandatud.ipynb` | ATEPP 4-klassi klassifikaatori treenimine ja hindamine. Mudeli arhitektuur (maskeeritud keskmistamisega klassifitseerimispea), andmestiku ettevalmistus, kahefaasiline treenimine, tulemuste visualiseerimine. |
| `2EestiSoomeKlassifikaator.ipynb` | Eesti-Soome rahvamuusika 2-klassilise mudeli treenimine. MusicXML-failide teisendamine MIDI-vormingusse (music21), tempo normaliseerimine, 5-kordne ristvalideerimine, bar-tokeni ablatsioonikatse. |
| `6Klassi.ipynb` | 6-klassilise kombineeritud mudeli treenimine (ATEPP 4 heliloojat + 2 rahvamuusika klassi). Ristvalideerimine ja tulemuste võrdlus. |
| `Atepp_Attention_rollout.ipynb` | Klassikalise muusika kumulatiivse tähelepanu analüüs. Rollout-funktsioonid (3, 6 ja 12 kihti), klaverirulli visualiseerimine, kontsentreerituse mõõdikud (Gini koefitsient, entroopia, kurtoosis), helikõrguse ulatuse statistiline analüüs (Mann-Whitney U test, χ²-test). |
| `AttentionRollout_Rahvamuusika.ipynb` | Rahvamuusika kumulatiivse tähelepanu analüüs. Tokenite joondamine originaalnootidega (scipy cdist), värvitud partituuride eksportimine MusicXML-failidena. |
| `requirements.txt` | Vajalikud Python teegid. |

## Eeltreenitud mudel

Töös kasutatakse Chou jt (2024) eeltreenitud MidiBERT-Piano mudelit (noodistuse versioon): https://github.com/wazenmai/MIDI-BERT

Eeltreenitud mudeli kaalufail (`pretrain_model.ckpt`) tuleb alla laadida ülaltoodud repositooriumist.

## Peenhäälestatud mudelid

Eksperimentide käigus treenitud mudelid:

| Fail | Kirjeldus |
|------|-----------|
| `atepp_parandatud_final.pt` | ATEPP 4-klassi klassifikaatori lõplik mudel |
| `final_folk_model.pt` | Eesti-Soome 2-klassilise mudeli lõplik mudel |
| `final_6klassi_model.pt` | 6-klassilise kombineeritud mudeli lõplik mudel |

Kaalufailid on kättesaadavad: https://drive.google.com/drive/u/0/folders/1aIqpfe8gh3E9eOUEUVgzxkpv2G0GbQTU

## Tarkvaranõuded

Katsed teostati Google Colab keskkonnas (NVIDIA T4 GPU, 15 GB VRAM).

```
pip install -r requirements.txt
```

Notebookid kloonivad automaatselt MidiBERT-Piano repositooriumi, mis sisaldab CP-tokenisaatorit ja mudeli arhitektuuri.

## Käivitamine

1. Laadida notebook Google Colabisse
2. Ühendada Google Drive (notebookid eeldavad andmete ja mudelite asukohta Drive'is)
3. Käivitada lahtrid järjest ülalt alla

Andmete ja mudelite asukohad on defineeritud muutujatena notebookide alguses ning vajavad kohandamist vastavalt kasutaja Google Drive'i struktuurile.

## Andmestikud

- **ATEPP** (Zhang jt, 2022): allalaetav autorite repositooriumist
- **Eesti rahvamuusika**: Eesti Pärimusmuusika Keskuse kinnine andmestik (folk.ee), ei ole avalikult kättesaadav
- **Soome rahvamuusika**: eSävelmät andmebaas (https://esavelmat.jyu.fi/collection_download.html)