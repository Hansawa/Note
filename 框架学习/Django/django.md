## Django 安装与启动

```
> pip install django
> django-admin startproject [proj_name]
> python manage.py runserver
```

## apps

在网站上完成某一功能的应用程序，用来区分不同的业务域，使功能划分更清晰，解耦合

```
> python manage.py startapp [app_name]
```



## 创建与激活模型

模型：数据库中的表结构

迁移文件：根据模型的变化产生的相应的 sql 代码

迁移：执行迁移文件

1. 在 model.py 中定义模型
2. 在 setting.py 中注册对应的 appConfig
3. python manage.py makemigrations
4. python manage.py migrate

## 通过 django 提供的 api 对数据库进行操作

```
python manage.py shell

```

