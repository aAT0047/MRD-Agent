# MRD-Agent

## ABSTRACT

### Motivation
Minimal residual disease (MRD) detection holds significant value in the treatment and prognostic evaluation of cancer. However, the underlying circulating tumour DNA (ctDNA) mutations exhibit high heterogeneity both inter- and intra-samples, necessitating customised parameter configurations to achieve stable detection performance. Additionally, small variant detection pipelines commonly encompass at least two key steps: an upper-layer preliminary detection step and a lower-layer filtering step, each involving multiple parameters that are intricately coupled across steps. Overly stringent thresholds in the upper-layer detection step markedly increase the false-negative rate, whereas overly permissive thresholds complicate the subsequent filtering step and elevate false positives. Existing parameter optimisation approaches often fail to incorporate a unified dynamic mechanism to balance false-negative and false-positive rates under real-time feedback conditions, thereby impeding stable ctDNA-based MRD detection.

### Results
To address these challenges, we propose MRD-Agent, which integrates an ADMM (Alternating Direction Method of Multipliers) module into a DQN (Deep Q-Network) framework. This design enables the agent to dynamically adjust multiple constraints across the detection and filtering steps, achieving optimal parameter configurations through iterative optimisation. Furthermore, a meta-learning model is introduced to facilitate rapid parameter recommendations for highly heterogeneous samples. Experiments on both real-world and simulated datasets demonstrate that MRD-Agent achieves superior stability compared with existing software, with a root mean square error (RMSE) of 6.2% and a variance of 0.47% based on F1-measure. These findings indicate that MRD-Agent effectively balances high sensitivity and high specificity for large-scale detection tasks, substantially enhancing the stability of MRD detection.

![Figure 1](https://github.com/aAT0047/MRD-Agent/blob/main/pict/figure1.png)
## Installation

### Prerequisites
The following packages and software need to be installed before running **TMBstable**:

#### Python Libraries
Make sure you have the following Python libraries installed:
- `os`
- `csv`
- `math`
- `pysam`
- `numpy`
- `random`
- `argparse`
- `matplotlib`
- `sklearn`
- `scipy`
- `skmultilearn`
- `quickgt`
- `pytorch`

You can install the Python dependencies using `pip`:
```bash
pip install pysam numpy matplotlib sklearn scipy skmultilearn quickgt torch

## Data Access

### PACA-CA Project
The dataset used in this project is sourced from the **PACA-CA Project**, which can be accessed via a **DACO-authorised account** at the following URL:
[ICGC ARGO Platform](https://platform.icgc-argo.org/).

### Download Instructions
To download the required data files, you can use the `score-client` command-line tool. Below is an example command for downloading and processing the data:

```bash
bin/score-client view \
  --manifest /yourpath/Donor_cramTSVs/DO35116.tsv \
  --reference-file /yourpath/GRCh38_hla_decoy_ebv.fa.gz \
  --bed-query /yourpath/icgccram/bed/DO35116.bed \
  --output-dir cramdata \
  --output-format bam
