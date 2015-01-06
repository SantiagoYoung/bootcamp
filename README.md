# Bootcamp

Bootcamp是一个使用[Django][0]开发的社区网站.

这个应用包括以下内容:

* 动态 （无限滚动，活动通知，实时更新，评论，点赞）
* 博客 （基本博客功能，分页，标记，草稿）
* Q&A （对用户的答案或问题进行标记，投票，采纳）

## 使用技术

- Python 2.7
- Django 1.6.5
- Twitter Bootstrap 3
- jQuery 2

## 示例

Bootcamp已经部署在OpenShift [http://bootcamp.lichun.me/][1].


## 安装指南
1.确认机器已经安装Python2.7, pip

2.克隆这个代码:
```bash
git clone https://git.oschina.net/lichun19960112/Bootcamp.git
```
3.安装依赖包:
```bash
pip install -U -r requirements.txt
```

4.配置,修改settings.py文件连接数据库参数和关闭调试模式
```python
# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True
TEMPLATE_DEBUG = DEBUG

# Deployment OpenShift
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': os.environ['PGDATABASE'],
        'USER': os.environ['PGUSER'],
        'PASSWORD': 'QRNY6h61qSIU',
        'HOST': os.environ['PGHOST'],
    }
}
```

5.初始化数据库：
```bash
python manage.py syncdb
python manage.py migrate
```

6.运行:
```bash
python manage.py runserver
```

[0]: https://www.djangoproject.com/
[1]: http://bootcamp.lichun.me/