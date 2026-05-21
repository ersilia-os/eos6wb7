# Antimicrobial activity prediction against Klebsiella pneumoniae from public ChEMBL data

Bioactivity prediction of growth inhibition in Klebsiella pneumoniae, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-05-21.

## Information
### Identifiers
- **Ersilia Identifier:** `eos6wb7`
- **Slug:** `antimicrobial-activity-kpneumoniae`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Antimicrobial resistance`, `Pneumonia`
- **Target Organism:** `Klebsiella pneumoniae`
- **Tags:** `Gram-negative bacteria`, `ESKAPE`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `14`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Klebsiella pneumoniae from 13 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 13 sub-models. Recommended threshold: 0.896. |
| merged_mic_decoys_d | float | high | Probability from sub-model trained on MIC measurements merged across 11 ChEMBL assays (cutoff 10 uM; n=2830 incl. decoys). Recommended threshold: 0.895. |
| merged_mic_decoys_c | float | high | Probability from sub-model trained on MIC measurements merged across 4 ChEMBL assays (cutoff 10 uM; n=1140 incl. decoys). Recommended threshold: 0.884. |
| merged_iz_decoys_b | float | high | Probability from sub-model trained on inhibition zone diameter measurements merged across 6 ChEMBL assays (cutoff 10 mm; n=1130 incl. decoys). Recommended threshold: 0.912. |
| merged_mic_decoys_b | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 10 uM; n=900 incl. decoys). Recommended threshold: 0.885. |
| merged_mic_decoys_a | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 20 uM; n=590 incl. decoys). Recommended threshold: 0.876. |
| merged_iz_decoys_a | float | high | Probability from sub-model trained on inhibition zone diameter measurements merged across 10 ChEMBL assays (cutoff 20 mm; n=530 incl. decoys). Recommended threshold: 0.880. |
| merged_mic | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 10 uM; n=266). Recommended threshold: 0.451. |
| general_mic | float | high | Probability from sub-model trained on MIC measurements aggregated across 3460 ChEMBL assays (cutoff 10 uM; n=16492). Recommended threshold: 0.671. |
| general_iz | float | high | Probability from sub-model trained on inhibition zone diameter measurements aggregated across 423 ChEMBL assays (cutoff 20 mm; n=2971). Recommended threshold: 0.627. |

_10 of 14 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos6wb7](https://hub.docker.com/r/ersiliaos/eos6wb7)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos6wb7.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos6wb7.zip)

### Resource Consumption
- **Model Size (Mb):** `93`
- **Environment Size (Mb):** `1888`
- **Image Size (Mb):** `2180.55`

**Computational Performance (seconds):**
- 10 inputs: `38.2`
- 100 inputs: `38.69`
- 10000 inputs: `712.32`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos6wb7
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos6wb7
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
