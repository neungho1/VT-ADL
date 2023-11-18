# VT-ADL : A Vision Transformer Network for Image Anomaly Detection and Localization
*저자 - Pankaj Mishra, Ricardo Verk, Daniele Fornasier, Claudio Piciarelli, Gian Luca Foresti*

<img src="image/bt_anomaly_dataset.png">

**개요**- *transformer 기반의 이미지 이상 탐지 및 위치 지정 네트워크를 제시합니다. 우리가 제안하는 모델은 reconstruction 기반 접근법과 patch embedding의 조합입니다. transformer networks의 사용은 embedded patches의 공간 정보를 보존하는 데 도움이 되며, 이는 나중에 Gaussian mixture density network에 의해 처리되어 이상한 영역을 localize합니다. 또한, 우리는 실제 산업 이상 데이터셋인 BTAD를 공개합니다. 우리의 결과는 MNIST와 MVTec와 같은 공개적으로 이용 가능한 데이터셋을 사용하여 다른 최첨단 알고리즘과 비교됩니다.*

# Network
네크워크는 [Vision Transformer](https://openreview.net/pdf?id=YicbFdNTTy)에서 영감을 받았습니다. 이미지 이상 탐지 및 위치 파악을 위해 Transnformer 네트워크를 조정합니다.
<img src="image/Ano-VT.png">

# BeanTech Anomaly Detection Dataset - BTAD 
출처: [BeanTech srl](https://www.beantech.it)
라이센스 유형: [CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/legalcode)

데이터 세트에는 세 가지 산업용 제품의 RGB 이미지가 포함되어 있습니다.– [Scan to download](https://avires.dimi.uniud.it/papers/btad/btad.zip)
<img src="image/btad-QR.png">

이미지는 산업용 이미지 수집 시스템에서 캡처한 후 데이터 소유자(Beantech)의 개인 정보 보호 정책을 존중하기 위해 잘라내고 로그 변환을 적용했습니다.  나중에 상업적으로 이용 가능한 주석 도구인 ["SuperAnnotate"](https://superannotate.com/)를 사용하여 데이터에 수동으로 주석을 달아 픽셀 단위의 정확한 ground_truth가 추가되었습니다.

* 제품 1 :  1600x1600픽셀의 이미지 400장 포함
* 제품 2 :  600x600픽셀의 이미지 1000장 포함
* 제품 3 :  800x600픽셀의 이미지 399장 포함

# Results
* **MVTec Dataset** - *실제 이상 현상 데이터 세트입니다. 다양한 질감과 개체 카테고리의 5354개의 고해상도 컬러 및 회색 이미지가 포함되어 있습니다.*
<img src="image/mvtec_predicted.png">

* **BTAD Dataset** - *산업용 제품의 고해상도 1.8K RGB 이미지로 구성됩니다.*
<img src="image/btad-results.png">

# Ablation
* *혼합 모델에서 Gaussian’s number의 선택은 Gaussian’s number of의 증가에 따라 정당화됩니다.*
* *PRO Score가 먼저 증가한 다음 일정해집니다.*
<img src="image/no-of-gaus-ablation.png">

## Regularization
* * transformer에서 인코딩된 features에 Gaussian noise가 추가되어 정규화되었습니다.* 
* *Noise가 추가된 PRO score는 0.897 Noise가 없는 경우 0.807*

# Train (Command Line)
` python train.py -p "물건이름" ` BTAD dataset 종류 01,02,03

# Cite
이 데이터셋을 사용할 경우, 아래의 참조를 사용하여 인용:
 
```
P. Mishra, R. Verk, D. Fornasier, C. Piciarelli, G.L. Foresti
"VT-ADL: A Vision Transformer Network for Image Anomaly Detection and Localization"
30th IEEE/IES International Symposium on Industrial Electronics (ISIE)
Kyoto, Japan, June 20-23, 2021
```

BibTeX:
```

@inproceedings{

        mishra21-vt-adl,
        author = {Mishra, Pankaj and Verk, Riccardo and Fornasier, Daniele and Piciarelli, Claudio and Foresti, Gian Luca},
        title = {{VT-ADL}: A Vision Transformer Network for Image Anomaly Detection and Localization},
        booktitle = {30th IEEE/IES International Symposium on Industrial Electronics (ISIE)},
        year = {2021},
        month = {June},
        location = {Kyoto, Japan}
	}
```
