# MAI-Lab 4번 서버 파일 설명서

var/www/html/backend/ 

위 경로에 알렉스원 서버에 사용되는 코드들이 있습니다.

파일 탐색기에서 var여실려면 other locations로 여세요

하위 폴더별로 설명하겠습니다

>ocr1 폴더는 체크박스 설문지 인식용 프로그램이 있는 폴더입니다.
>
>최신버전으로 업데이트를 안해서 연구실 컴퓨터에 있는 최신 버전으로 업데이트가 필요할거에요
-------

>ocr2 폴더가 주로 작업하실 배뇨일지 설문지 인식 프로그램이 있는 폴더입니다.
>
>서버 구동에 필요한 프로그램들이 있습니다.
>
>accuracy_test.py는 현재 프로그램의 정확도를 측정해 주는 프로그램입니다.
>
>ocr2/dataset/test_data에 있는 이미지들 대상으로 정확도를 측정합니다.
>
>그냥 돌리면 안되고 server.py를 실행한 상태에서만 동작합니다.
>
>측정된 정확도는 save_file/accuracy_test폴더에서 확인 가능합니다.
>
>server.py와 alexone 뭐시기.py 2개의 프로그램은 알렉스원 홈페이지 구동에 필요합니다.
>
>3개를 동시에 활성화하면 알렉스원 홈페이지에 이미지를 올린 뒤 엑셀파일을 받을 수 있습니다.
>
>>ocr2/dataset 폴더에는 데이터들이 저장되어있습니다.
>>
>>base image에는 인식에 필요한 빈 설문지가 있습니다.
>>
>>배뇨일지 설문지의 4일차 설문지는 나머지 1,2,3일차 설문지와 상단의 포멧이 살짝 달라서 따로 처리해야 하므로 두종류의 포멧이 있습니다.
>>
>>original 폴더에는 스캔된 설문지가 있습니다.
>>
>>recognition_dataset에는 트레이닝에 필요한 숫자 이미지들이있습니다
>>
>>set1은 병원 설문지에서 얻은 이미지들
>>
>>set2,3,4는 실험실에서 연구원분들이 손으로 쓴 이미지들입니다.
>>
>>set1을 주로 사용해서 트레이닝하길 추천합니다.
>>
>>test_data는 정확도 테스트에 필요한 레이블과 이미지들 입니다.
>>
-----
>>ocr2/src폴더에는 프로그램 구동에 필요한 파일들이 있습니다.
>>
>>inference폴더에 있는 파일들은 ocr2폴더에 있는 서버.py를 구동할때 작동되는 프로그램입니다.
>>
>>>inference 폴더의 각 하위폴더별로 기능을 보면 프로그램 작동 방식에 대해 알 수 있습니다.
>>>
>>>corner_detection 폴더의 내용물은 작성된 배뇨 일지의 코너를 인식해서 잘라주는 역할을 합니다.
>>>
>>>작성된 배뇨일지의 코너를 찾아서 작성되지 않은 원본 배뇨일지와 겹침으로써 모델이 더 쉽게 작성된 부분을 인식할 수 있습니다.
>>>
>>>이를 위해 U-net을 사용하여 설문지 모서리 부분을 찾아냅니다.
>>>
>>>perspective_optimizer는 디텍션된 코너를 원본 이미지의 코너와 겹쳐지게 해 주는 부분입니다.
>>>
>>>bbox_detection, bbox_crop은 각각 설문지 내부의 연속된 숫자 영역을 yolov5로 디텍션 해 주는 부분 그리고 디텍션 된 부분을 자르는 부분입니다.
>>>
>>> denoise_images, crop_denoise_images는 각각 잘려진 숫자 영역을 denoising해서 필요없는 선을 제거해주는 부분, 제거된 뒤 숫자이미지 크기에 딱 맞게 crop해주는 부분입니다.
>>>
>>>dan_recognition은 이렇게 얻은 숫자이미지들을 인식해 디지털 숫자로 변환하는 부분입니다
>>>
>>>excel_demo는 결과물을 엑셀로 만들어주는 부분입니다.
>>
>>train 폴더에는 위 과정들에 필요한 프로그램을 학습시키는 코드가 있습니다.
>>>
>>>이중에 dan_recognition을 참고해서 코딩하시면 될 것 같습니다.
>>>
>>>dan_recognition의 중요한 파일들에는 제가 주석으로 설명을 달아 두었으니 참고하시면 될겁니다.
>>>
>>>
