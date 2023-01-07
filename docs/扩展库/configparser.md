<!-- MDTOC maxdepth:6 firsth1:1 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [configparser](#configparser)   
   - [实例初始化](#实例初始化)   
   - [从文件读取配置](#从文件读取配置)   
   - [从字符串中读取配置](#从字符串中读取配置)   
   - [从字典读取配置](#从字典读取配置)   
   - [获取所有节sections/节中选项](#获取所有节sections节中选项)   
   - [取值](#取值)   
   - [导出配置](#导出配置)   
   - [常用操作](#常用操作)   

<!-- /MDTOC -->

# configparser

* <https://docs.python.org/3/library/configparser.html>


## 实例初始化

```
import configparser
config = configparser.ConfigParser()
```

## 从文件读取配置

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')
```

## 从字符串中读取配置

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')

config.read_string("[topsecret.server.com]\nPort=48484")
config['topsecret.server.com']['Port']
# '48484'

```

## 从字典读取配置

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')

config.read_dict({"topsecret.server.com": {"Port": 21212}})
config['topsecret.server.com']['Port']
# '21212'
```

* 支持多种读取配置方式接连使用，后者覆盖前者


## 获取所有节sections/节中选项

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')
print(config.sections())

# ['main', 'othersections']
for ss in config.sections():
  for opt in config[ss]:
    print(ss, opt, config[ss][opt])
```


## 取值

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')

# parser['section']['option']

config.get('ss', 'goodLuck', fallback="yes")
config.getint('ss', 'goodLuck', fallback=1)
config.getboolean('ss', 'goodLuck', fallback=True)
config.getfloat('ss', 'goodLuck', fallback=1.2)

```

* fallback提供默认值



## 导出配置

```
import configparser
config = configparser.ConfigParser()
config.read('example.ini')

with open('example.ini', 'w') as configfile:
  config.write(configfile)
```


## 常用操作

```

sections() 得到所有的section，并以列表的形式返回
options(section) 得到该section的所有option (key值)
items(section) 得到该section的所有键值对，返回结果是列表中包含的元祖
get(section, option) 得到section中option的值，返回为string类型，指定标签下面的key对应的value值
getint(section, option) 得到section中的option值，返回为int类型
has_section(section) 判断指定的option是否存在
has_option(section,option)判断指定option中的option是否存在
add_section(str) 往配置文件中添加section
set(section, name, value) 在section下设置name=value
remove_option(section,option)删除指定节点section中的option
remove_section(section)删除指定的section
read(filename) 读取配置文件， read(’./config.ini’)
write(obj_file) 写入配置文件 ，write(open(“config.ini”, “w”))

```























---
