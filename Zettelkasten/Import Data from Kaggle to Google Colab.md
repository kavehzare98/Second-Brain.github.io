202406121153
Status: #learning
Tags: [Machine Learning], [Data Science], [Kaggle]
# How to import Data from Kaggle to Google Colab

### Easiest way to download Kaggle data in Google Colab

Please follow the steps below to download and use Kaggle data within Google Colab:

1. Go to your account, Scroll to API section and Click **Expire API Token** to remove previous tokens

2. Click on **Create New API Token** - It will download ***kaggle.json*** file on your machine.

3. Go to your Google Colab project file and run the following commands:

**First Step:**
```bash
! pip install -q kaggle
```
****
**Second Step:**
```python
from google.colab import files
files.upload()
```

- Also: Choose the ***kaggle.json*** file that you downloaded
****
**Third Step:** Make directory named kaggle and copy ***kaggle.json*** file there.

```bash
! mkdir ~/.kaggle
! cp kaggle.json ~/.kaggle/
```

****
**Fourth Step:** Change the permissions of the file.
```bash
! chmod 600 ~/.kaggle/kaggle.json
! kaggle datasets list  
```

**That's all!** You can check if everything's okay by running this command.
### Download Data

``` bash
! kaggle competitions download -c 'name-of-competition'
```

Use unzip command to **unzip the data**:

**For example,** create a directory named train,

``` bash
! mkdir train
```

unzip train data there,

``` bash
! unzip train.zip -d train
```
# References
Link: https://www.kaggle.com/discussions/general/74235