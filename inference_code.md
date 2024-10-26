# inference.py
---
>* sh 파일에서 인자로 받기 때문에 inference.py 내에서 수정을 코드는 없음.
>* 분석한 결과가 __"현재경로/result_dir/predict/"__ 내에 저장됨.
>* ultralytics가 설치되어 있지 않다면, 따로 설치 필요.


```python
# pip install ultralytics
```


```python
import argparse
from ultralytics import YOLO

def run_inference(model_path,test_dir,result_dir):
    model_path = args.model_path
    test_dir = args.test_dir
    result_dir = args.result_dir
    
    # 모델 정의
    model = YOLO(model_path)
    
    # 모델 예측 결과 저장(현재경로/result_dir/predict 경로 내에 결과 저장)
    results = model.predict(source=test_dir, project=result_dir, show_conf=False, save_txt=True, save=True)

if __name__ == "__main__":
    parser = argparse.ArgumentParser(description='교통CCTV 돌발상황 분석 프로그램')

    parser.add_argument('--model_path', type=str, required=True, help='모델 파일 경로를 입력하세요.')
    parser.add_argument('--test_dir', type=str, required=True, help='분석할 이미지 디렉토리 경로를 입력하세요.')
    parser.add_argument('--result_dir', type=str, required=True, help='분석한 결과가 저장될 디렉토리 이름을 입력하세요.')    

    args = parser.parse_args()
    
    run_inference(args.model_path, args.test_dir,args.result_dir)

```

    usage: ipykernel_launcher.py [-h] --model_path MODEL_PATH --test_dir TEST_DIR
    ipykernel_launcher.py: error: the following arguments are required: --model_path, --test_dir
    


    An exception has occurred, use %tb to see the full traceback.
    

    SystemExit: 2
    


    C:\Users\tjdgh\anaconda3\lib\site-packages\IPython\core\interactiveshell.py:3468: UserWarning: To exit: use 'exit', 'quit', or Ctrl-D.
      warn("To exit: use 'exit', 'quit', or Ctrl-D.", stacklevel=1)
    

# run_inference.sh
---
>* __model_path__
    * 모델 파일이 존재하는 경로를 입력
>* __test_dir__
    * 분석할 이미지가 존재하는 디렉토리 경로를 입력
>* __result_dir__
    * 분석한 결과가 저장될 디렉토리 이름
---
* __"C:\\Users\\tjdgh\\anaconda3\\envs\\sejong\\python.exe"를 통해 python의 경로를 직접 설정.__
    * 여러 python이 존재해서 직접 설정해주었지만, 해당사항이 없다면 생략 가능.
    * <u>__필요하다면 사용자의 python 경로로 변경해야 함.__</u>


```python
C:\\Users\\tjdgh\\anaconda3\\envs\\sejong\\python.exe inference.py \
--model_path ./best.pt \
--test_dir ./new_data_test/images/ \
--result_dir 무단횡단금지팀 \
```
