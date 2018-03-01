# 專案指引

Django 2 官網所發佈之 Tutorials 文件，實作成果。

# 專案特性
 - 將預設的「資料庫系統」，自 SQLite 改成 PostgreSQL
 - 使用 Docker Compose 實作專案
 - 專案之 Models 以 StarUML 的 Class Diagram 記錄

---

# 建置專案開發環境作業

### 建立「專案目錄」
```bash
$ mkdir django2_tutorials && cd $_
```

### 複製「專案模版」檔案
```bash
$ cp ~/_mySDK/Django/* .
$ cp ~/_mySDK/Django/.gitignore .
```

此時「專案目錄」中應有四個檔案：
 - requirements.txt
 - Dockerfile
 - docker-compose.yml
 - .gitignore

### 設定虛擬環境
```bash
$ workon django2
```

### 安裝 Django 套件
```bash
$ pip install -r requirements.txt
```

### 建立「Django 專案」
```bash
$ django-admin startproject web_site .
```

### 驗證「Django 專案」已能正常運作
```bash
$ ./manage.py runserver
```

Web URL: http://127.0.0.1:8000/

### 建立「Django App」
```bash
./manage.py startapp polls
```

### 修訂 Django 專案的「設定」
```python
ALLOWED_HOSTS = [
    'testserver',
    '127.0.0.1',
]

INSTALLED_APPS = [
    ...,
    
    'polls',
]

DATABASES = {
   'default': {
       'ENGINE': 'django.db.backends.postgresql_psycopg2',
       'NAME': 'postgres',
       'USER': 'postgres',
       'PASSWORD': 'Passw0rd',
       'HOST': 'db'
   }
}

# DATABASES = {
#     'default': {
#         'ENGINE': 'django.db.backends.sqlite3',
#         'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
#     }
# }
```

### 建立 Docker Image: Web Service
```bash
$ docker-compose build
```

### 透過 Docker Compose 啟動專案所有所需 Service
```bash
$ docker-compose up
```

【驗證】：
```bash
URL: http://127.0.0.1:8000/
```


---
 
# 參考資料
 - [Django 2 Getting started](https://docs.djangoproject.com/en/2.0/intro/) 
 