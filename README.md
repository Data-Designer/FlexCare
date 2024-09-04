# FlexCare
Source code for ***FlexCare: Leveraging Cross-Task Synergy for Flexible Multimodal Healthcare Prediction*** published in KDD 2024.

📄Paper is available at: <a href="https://dl.acm.org/doi/abs/10.1145/3637528.3671974" target="_blank">ACM DL</a> or <a href="https://arxiv.org/abs/2406.11928" target="_blank">arXiv</a>

![image](pic/framework.png)

Requirements
----
This project is run in a conda virtual environment on Ubuntu 20.04 with CUDA 11.1. 
+ torch==1.10.1+cu111
+ Python==3.7.9
+ transformers==4.30.2
+ tokenizers==0.13.3
+ huggingface-hub==0.16.4

Data preparation
----
You will first need to request access for MIMIC dataset:
+ MIMIC-IV 2.0 https://physionet.org/content/mimiciv/2.0/
+ MIMIC-CXR-JPG 2.0.0 https://physionet.org/content/mimic-cxr-jpg/2.0.0/
+ MIMIC-IV-NOTE 2.2 https://physionet.org/content/mimic-iv-note/2.2/

Then follow the steps in [mimic4extract](mimic4extract/README.md) to build datasets for all tasks in directory [data].

In addition, we use _biobert-base-cased-v1.2_ as the pretrained text encoder, please download files in https://huggingface.co/dmis-lab/biobert-base-cased-v1.2, and put them into the directory [mymodel/pretrained]

Model training
----
``
python main_mt.py --data_path data --ehr_path data/ehr --cxr_path data/cxr --task in-hospital-mortality,length-of-stay,decompensation,phenotyping,readmission,diagnosis --epochs 25 --lr 0.0001 --device {gpu id} --seed {40,42,44,46,48}
``

Citation
----
```
@inproceedings{xu2024flexcare,
  title={FlexCare: Leveraging Cross-Task Synergy for Flexible Multimodal Healthcare Prediction},
  author={Xu, Muhao and Zhu, Zhenfeng and Li, Youru and Zheng, Shuai and Zhao, Yawei and He, Kunlun and Zhao, Yao},
  booktitle={Proceedings of the 30th ACM SIGKDD Conference on Knowledge Discovery and Data Mining},
  pages={3610--3620},
  year={2024}
}
```
