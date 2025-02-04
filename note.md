## Github Repo

- https://github.com/AmadeusITGroup/Moire-Pattern-Detection
- https://github.com/cong-yang/MoireDet

## virtualenv

- `pip install virtualenv`
- `virtualenv env -p E:\sys\services\Python\Python311\python.exe`
- `.\env\Scripts\activate`
- `deactivate`
- `python -m pip freeze > requirements.txt` -> backup package
- `pip install -r requirements.txt` -> restorage package
- `python manage.py makemigrations`
- `python manage.py migrate` -> tạo database, nếu chưa có sẵn database
- `python manage.py runserver 0.0.0.0:8000` -> start for all ip

## **Note - Resize Images to WIDTH = 1000 and HEIGHT = 750**

### 1. create virtual env

```bash
pip install virtualenv
virtualenv env -p E:\sys\services\Python\Python311\python.exe

.\env\Scripts\activate
python.exe -m pip install --upgrade pip

pip install -r requirements.txt

deactivate
```

### 3. create the wavelet decomposed training dataset from the captured images

`python createTrainingData.py positiveImages negativeImages train`

- train => `python ".\src\createTrainingData.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" 0`
- test => `python ".\src\createTrainingData.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" 1`

### 4. train the CNN model using training images

`python train.py positiveImages negativeImages trainingDataPositive trainingDataNegative epochs`

- train => `python ".\src\train.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainingDataPositive" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainingDataNegative" 1`
- test => `python ".\src\train.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainDataPositive" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainDataNegative" 1`

### 5. test the CNN model using test images

`python test.py moirePattern3CNN_.h5  positiveImages negativeImages`

- test => `python ".\src\test.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\moirePattern3CNN_.h5" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages"`

## Sample Execute

```bash
PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> virtualenv env -p E:\sys\services\Python\Python311\python.exe

PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> .\env\Scripts\activate
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python.exe -m pip install --upgrade pip
Requirement already satisfied: pip in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (25.0)
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> pip install -r requirements.txt
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>

(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python.exe -m pip install --upgrade pip
Requirement already satisfied: pip in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (25.0)
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> pip install -r requirements.txt
Requirement already satisfied: absl-py==2.1.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 1)) (2.1.0)
Requirement already satisfied: astunparse==1.6.3 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 2)) (1.6.3)
Requirement already satisfied: certifi==2025.1.31 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 3)) (2025.1.31)
Requirement already satisfied: charset-normalizer==3.4.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 4)) (3.4.1)
Requirement already satisfied: contourpy==1.3.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 5)) (1.3.1)
Requirement already satisfied: cycler==0.12.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 6)) (0.12.1)
Requirement already satisfied: flatbuffers==25.1.24 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 7)) (25.1.24)
Requirement already satisfied: fonttools==4.55.8 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 8)) (4.55.8)
Requirement already satisfied: gast==0.6.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 9)) (0.6.0)
Requirement already satisfied: google-pasta==0.2.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 10)) (0.2.0)
Requirement already satisfied: grpcio==1.70.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 11)) (1.70.0)
Requirement already satisfied: h5py==3.12.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 12)) (3.12.1)
Requirement already satisfied: idna==3.10 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 13)) (3.10)
Requirement already satisfied: imageio==2.37.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 14)) (2.37.0)
Requirement already satisfied: joblib==1.4.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 15)) (1.4.2)
Requirement already satisfied: keras==3.5.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 16)) (3.5.0)
Requirement already satisfied: Keras-Applications==1.0.8 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 17)) (1.0.8)
Requirement already satisfied: Keras-Preprocessing==1.1.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 18)) (1.1.2)
Requirement already satisfied: kiwisolver==1.4.8 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 19)) (1.4.8)
Requirement already satisfied: lazy_loader==0.4 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 20)) (0.4)
Requirement already satisfied: libclang==18.1.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 21)) (18.1.1)
Requirement already satisfied: Markdown==3.7 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 22)) (3.7)
Requirement already satisfied: markdown-it-py==3.0.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 23)) (3.0.0)
Requirement already satisfied: MarkupSafe==3.0.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 24)) (3.0.2)
Requirement already satisfied: matplotlib==3.10.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 25)) (3.10.0)
Requirement already satisfied: mdurl==0.1.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 26)) (0.1.2)
Requirement already satisfied: ml-dtypes==0.4.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 27)) (0.4.1)
Requirement already satisfied: namex==0.0.8 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 28)) (0.0.8)
Requirement already satisfied: networkx==3.4.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 29)) (3.4.2)
Requirement already satisfied: numpy==2.0.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 30)) (2.0.2)
Requirement already satisfied: opt_einsum==3.4.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 31)) (3.4.0)
Requirement already satisfied: optree==0.14.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 32)) (0.14.0)
Requirement already satisfied: packaging==24.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 33)) (24.2)
Requirement already satisfied: pillow==11.1.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 34)) (11.1.0)
Requirement already satisfied: protobuf==5.29.3 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 35)) (5.29.3)
Requirement already satisfied: Pygments==2.19.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 36)) (2.19.1)
Requirement already satisfied: pyparsing==3.2.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 37)) (3.2.1)
Requirement already satisfied: python-dateutil==2.9.0.post0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 38)) (2.9.0.post0)
Requirement already satisfied: PyWavelets==1.8.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 39)) (1.8.0)
Requirement already satisfied: PyYAML==6.0.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 40)) (6.0.2)
Requirement already satisfied: requests==2.32.3 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 41)) (2.32.3)
Requirement already satisfied: rich==13.9.4 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 42)) (13.9.4)
Requirement already satisfied: scikit-image==0.25.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 43)) (0.25.1)
Requirement already satisfied: scikit-learn==1.6.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 44)) (1.6.1)
Requirement already satisfied: scipy==1.15.1 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 45)) (1.15.1)
Requirement already satisfied: six==1.17.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 46)) (1.17.0)
Requirement already satisfied: tensorboard==2.18.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 47)) (2.18.0)
Requirement already satisfied: tensorboard-data-server==0.7.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 48)) (0.7.2)
Requirement already satisfied: tensorflow==2.18.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 49)) (2.18.0)
Requirement already satisfied: tensorflow-io-gcs-filesystem==0.31.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 50)) (0.31.0)
Requirement already satisfied: tensorflow_intel==2.18.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 51)) (2.18.0)
Requirement already satisfied: termcolor==2.5.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 52)) (2.5.0)
Requirement already satisfied: threadpoolctl==3.5.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 53)) (3.5.0)
Requirement already satisfied: tifffile==2025.1.10 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 54)) (2025.1.10)
Requirement already satisfied: typing_extensions==4.12.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 55)) (4.12.2)
Requirement already satisfied: urllib3==2.3.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 56)) (2.3.0)
Requirement already satisfied: Werkzeug==3.1.3 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 57)) (3.1.3)
Requirement already satisfied: wrapt==1.17.2 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from -r requirements.txt (line 58)) (1.17.2)
Requirement already satisfied: wheel<1.0,>=0.23.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from astunparse==1.6.3->-r requirements.txt (line 2)) (0.45.1)
Requirement already satisfied: setuptools>=41.0.0 in d:\vihat\github\vhs-fork\moire-pattern-detection\env\lib\site-packages (from tensorboard==2.18.0->-r requirements.txt (line 47)) (75.7.0)
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python ".\src\createTrainingData.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" 0
positive samples: 3
negative samples: 4
training image rotated
training image rotated
training image rotated
Total positive files after augmentation:  9
Total negative files after augmentation:  12
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python ".\src\createTrainingData.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" 1
positive samples: 3
negative samples: 4
training image rotated
training image rotated
training image rotated
Total positive files after augmentation:  9
Total negative files after augmentation:  12
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python ".\src\train.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainingDataPositive" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainingDataNegative" 1
2025-02-04 11:01:34.336403: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
2025-02-04 11:01:36.688117: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
positive samples: 12
negative samples: 16
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\284_letterbox1024_LL.tiff'
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\284_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\284_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\350_letterbox1024_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\350_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\350_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\355_letterbox1024_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\355_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataPositive\\355_letterbox1024_180_FLIP_LL.tiff'
positive data loaded.
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\0_letterbox1024_LL.tiff'
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\0_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\0_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\14_letterbox1024_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\14_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\14_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\22_letterbox1024_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\22_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\22_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\37_letterbox1024_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\37_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainingDataNegative\\37_letterbox1024_180_FLIP_LL.tiff'
negative data loaded.
Total Samples Loaded:  0
[[0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 ...
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]]
[[0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 ...
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]]
[[0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]]
25
25
25
3
3
num_train_samples 25
2025-02-04 11:01:39.911633: I tensorflow/core/platform/cpu_feature_guard.cc:210] This TensorFlow binary is optimized to use available CPU instructions in performance-critical operations.
To enable the following instructions: AVX2 FMA, in other operations, rebuild TensorFlow with the appropriate compiler flags.
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\ops\nn.py:545: UserWarning: You are using a softmax over axis -1 of a tensor of shape (None, 1). This axis has size 1. The softmax operation will always return the value 1, which is likely not what you intended. Did you mean to use a sigmoid instead?
  warnings.warn(
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\losses\losses.py:27: SyntaxWarning: In loss categorical_crossentropy, expected y_pred.shape to be (batch_size, num_classes) with num_classes > 1. Received: y_pred.shape=(None, 1). Consider using 'binary_crossentropy' if you only have 2 classes.
  return self.fn(y_true, y_pred, **self._fn_kwargs)
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 15s/step - accuracy: 1.0000 - loss: 0.0000e+00
Epoch 1: val_loss improved from inf to 0.00000, saving model to checkPoint/Weights-001--0.00000.keras
1/1 ━━━━━━━━━━━━━━━━━━━━ 17s 17s/step - accuracy: 1.0000 - loss: 0.0000e+00 - val_accuracy: 1.0000 - val_loss: 0.0000e+00
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 132ms/step - accuracy: 1.0000 - loss: 0.0000e+00
WARNING:absl:You are saving your model as an HDF5 file via `model.save()` or `keras.saving.save_model(model)`. This file format is considered legacy. We recommend using instead the native Keras format, e.g. `model.save('my_model.keras')` or `keras.saving.save_model(model, 'my_model.keras')`.
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\ops\nn.py:545: UserWarning: You are using a softmax over axis -1 of a tensor of shape (3, 1). This axis has size 1. The softmax operation will always return the value 1, which is likely not what you intended. Did you mean to use a sigmoid instead?
  warnings.warn(
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 266ms/step
confusion matrix (test / validation)
true positive:  3
false positive: 0
true negative:  0
false negative: 0


accuracy:  100.0000 %
precision: 100.0000 %
recall:  100.0000 %
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python ".\src\train.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainDataPositive" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\trainDataNegative" 1
2025-02-04 11:02:29.365372: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
2025-02-04 11:02:31.857948: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
positive samples: 12
negative samples: 16
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\284_letterbox1024_LL.tiff'
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\284_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 284_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\284_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\350_letterbox1024_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\350_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 350_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\350_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\355_letterbox1024_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\355_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 355_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataPositive\\355_letterbox1024_180_FLIP_LL.tiff'
positive data loaded.
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\0_letterbox1024_LL.tiff'
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\0_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 0_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\0_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\14_letterbox1024_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\14_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 14_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\14_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\22_letterbox1024_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\22_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 22_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\22_letterbox1024_180_FLIP_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\37_letterbox1024_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\37_letterbox1024_180_LL.tiff'
Error: Couldnt read the file 37_letterbox1024. Make sure only images are present in the folder
Exception: [Errno 2] No such file or directory: 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\src\\trainDataNegative\\37_letterbox1024_180_FLIP_LL.tiff'
negative data loaded.
Total Samples Loaded:  0
[[0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 ...
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]]
[[0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 ...
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]]
[[0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]]
25
25
25
3
3
num_train_samples 25
2025-02-04 11:02:35.266592: I tensorflow/core/platform/cpu_feature_guard.cc:210] This TensorFlow binary is optimized to use available CPU instructions in performance-critical operations.
To enable the following instructions: AVX2 FMA, in other operations, rebuild TensorFlow with the appropriate compiler flags.
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\ops\nn.py:545: UserWarning: You are using a softmax over axis -1 of a tensor of shape (None, 1). This axis has size 1. The softmax operation will always return the value 1, which is likely not what you intended. Did you mean to use a sigmoid instead?
  warnings.warn(
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\losses\losses.py:27: SyntaxWarning: In loss categorical_crossentropy, expected y_pred.shape to be (batch_size, num_classes) with num_classes > 1. Received: y_pred.shape=(None, 1). Consider using 'binary_crossentropy' if you only have 2 classes.
  return self.fn(y_true, y_pred, **self._fn_kwargs)
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 12s/step - accuracy: 1.0000 - loss: 0.0000e+00
Epoch 1: val_loss improved from inf to 0.00000, saving model to checkPoint/Weights-001--0.00000.keras
1/1 ━━━━━━━━━━━━━━━━━━━━ 14s 14s/step - accuracy: 1.0000 - loss: 0.0000e+00 - val_accuracy: 1.0000 - val_loss: 0.0000e+00
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 160ms/step - accuracy: 1.0000 - loss: 0.0000e+00
WARNING:absl:You are saving your model as an HDF5 file via `model.save()` or `keras.saving.save_model(model)`. This file format is considered legacy. We recommend using instead the native Keras format, e.g. `model.save('my_model.keras')` or `keras.saving.save_model(model, 'my_model.keras')`.
D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\ops\nn.py:545: UserWarning: You are using a softmax over axis -1 of a tensor of shape (3, 1). This axis has size 1. The softmax operation will always return the value 1, which is likely not what you intended. Did you mean to use a sigmoid instead?
  warnings.warn(
1/1 ━━━━━━━━━━━━━━━━━━━━ 0s 330ms/step
confusion matrix (test / validation)
true positive:  3
false positive: 0
true negative:  0
false negative: 0


accuracy:  100.0000 %
precision: 100.0000 %
recall:  100.0000 %
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> python ".\src\test.py" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\moirePattern3CNN_.h5" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\positiveImages" "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\negativeImages"
2025-02-04 11:04:09.196114: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
2025-02-04 11:04:11.768673: I tensorflow/core/util/port.cc:153] oneDNN custom operations are on. You may see slightly different numerical results due to floating-point round-off errors from different computation orders. To turn them off, set the environment variable `TF_ENABLE_ONEDNN_OPTS=0`.
E:\sys\services\Python\Python311\python.exe: can't open file 'D:\\vihat\\github\\vhs-fork\\Moire-Pattern-Detection\\createTrainingData.py': [Errno 2] No such file or directory
positive samples: 12
negative samples: 16
positive data loaded.
negative data loaded.
Total Samples Loaded:  30
[[0.77935225 0.78643727 0.78036439 ... 0.11032388 0.11234818 0.10931174]
 [0.10931174 0.11234818 0.11032388 ... 0.78036439 0.78643727 0.77935225]
 [0.50303644 0.71457487 0.69939274 ... 0.5688259  0.57085019 0.57388663]
 ...
 [0.         0.         0.         ... 0.         0.         0.        ]
 [0.         0.         0.         ... 0.         0.         0.        ]
 [0.         0.         0.         ... 0.         0.         0.        ]]
[[-0.01953819 -0.0017762  -0.0017762  ... -0.0017762  -0.00888099
   0.008881  ]
 [-0.00888094  0.00888105  0.00177626 ...  0.00177626  0.00177626
   0.01953825]
 [-0.34991118  0.03730018 -0.03019538 ...  0.0017762  -0.01243339
  -0.0017762 ]
 ...
 [ 0.          0.          0.         ...  0.          0.
   0.        ]
 [ 0.          0.          0.         ...  0.          0.
   0.        ]
 [ 0.          0.          0.         ...  0.          0.
   0.        ]]
[[0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [1.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]
 [0.]]
2025-02-04 11:04:16.074439: I tensorflow/core/platform/cpu_feature_guard.cc:210] This TensorFlow binary is optimized to use available CPU instructions in performance-critical operations.
To enable the following instructions: AVX2 FMA, in other operations, rebuild TensorFlow with the appropriate compiler flags.
Traceback (most recent call last):
  File "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\test.py", line 66, in <module>
    main(parse_arguments(sys.argv[1:]))
  File "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\test.py", line 45, in main
    CNN_model.load_weights(weights_file)
  File "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\keras\src\utils\traceback_utils.py", line 122, in error_handler
    raise e.with_traceback(filtered_tb) from None
  File "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\h5py\_hl\files.py", line 561, in __init__
    fid = make_fid(name, mode, userblock_size, fapl, fcpl, swmr=swmr)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "D:\vihat\github\vhs-fork\Moire-Pattern-Detection\env\Lib\site-packages\h5py\_hl\files.py", line 235, in make_fid
    fid = h5f.open(name, flags, fapl=fapl)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "h5py\\_objects.pyx", line 54, in h5py._objects.with_phil.wrapper
  File "h5py\\_objects.pyx", line 55, in h5py._objects.with_phil.wrapper
  File "h5py\\h5f.pyx", line 102, in h5py.h5f.open
FileNotFoundError: [Errno 2] Unable to synchronously open file (unable to open file: name = 'D:\vihat\github\vhs-fork\Moire-Pattern-Detection\src\moirePattern3CNN_.h5', errno = 2, error message = 'No such file or directory', flags = 0, o_flags = 0)
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
(env) PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection> deactivate
PS D:\vihat\github\vhs-fork\Moire-Pattern-Detection>
```
