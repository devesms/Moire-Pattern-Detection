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
