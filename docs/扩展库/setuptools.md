<!-- MDTOC maxdepth:6 firsth1:1 numbering:0 flatten:0 bullets:1 updateOnSave:1 -->

- [setuptools](#setuptools)   
   - [相关链接](#相关链接)   
   - [模板](#模板)   
   - [build](#build)   
   - [install](#install)   
   - [develop](#develop)   
   - [sdist](#sdist)   
   - [bdist](#bdist)   
   - [bdist_rpm](#bdist_rpm)   
   - [bdist_wininst](#bdist_wininst)   
   - [bdist_dumb](#bdist_dumb)   
   - [参考](#参考)   

<!-- /MDTOC -->
# setuptools

![20220408_154151_30](image/20220408_154151_30.png)

## 相关链接

* <https://pypi.org/project/setuptools/7.0/>
* <https://setuptools.pypa.io/en/latest/userguide/index.html>
* <https://github.com/pypa/setuptools>


* setuptools 是 distutils 增强版，不包括在标准库中。
* setuptools 扩展了很多功能，能够帮助开发者更好的创建和分发 Python 包。
* 大部分 Python 用户都会使用更先进的 setuptools 模块。



```
[root@centos8-crash ~/drgn.git]# python3 setup.py --help-commands
Standard commands:
  build             build everything needed to install
  build_py          "build" pure Python modules (copy to build directory)
  build_ext         build C/C++ extensions (compile/link to build directory)
  build_clib        build C/C++ libraries used by Python extensions
  build_scripts     "build" scripts (copy and fixup #! line)
  clean             clean up temporary files from 'build' command
  install           install everything from build directory
  install_lib       install all Python modules (extensions and pure Python)
  install_headers   install C/C++ header files
  install_scripts   install scripts (Python or otherwise)
  install_data      install data files
  sdist             create a source distribution (tarball, zip file, etc.)
  register          register the distribution with the Python package index
  bdist             create a built (binary) distribution
  bdist_dumb        create a "dumb" built distribution
  bdist_rpm         create an RPM distribution
  bdist_wininst     create an executable installer for MS Windows
  check             perform some checks on the package
  upload            upload binary package to PyPI

Extra commands:
  egg_info          create a distribution's .egg-info directory
  test              run unit tests after in-place build
  alias             define a shortcut to invoke one or more commands
  bdist_egg         create an "egg" distribution
  develop           install package in 'development mode'
  dist_info         create a .dist-info directory
  easy_install      Find/get/install Python packages
  install_egg_info  Install an .egg-info directory for the package
  rotate            delete older distributions, keeping N newest files
  saveopts          save supplied options to setup.cfg or other config file
  setopt            set an option in setup.cfg or another config file
  upload_docs       Upload documentation to PyPI
  compile_catalog   compile message catalogs to binary MO files
  extract_messages  extract localizable strings from the project code
  init_catalog      create a new catalog based on a POT file
  update_catalog    update message catalogs from a POT file

usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help

```




## 模板

```
setup(
    name="",
    version="0.0.1"
    packages=find_packages(include=["drgn", "drgn.*"]),
    package_data={"drgn": ["../_drgn.pyi", "py.typed"]},
    ext_modules=[Extension(name="_drgn", sources=[])],
    cmdclass={
        "build": build,
        "build_ext": build_ext,
        "egg_info": egg_info,
        "sdist": sdist,
        "test": test,
    },
    python_requires=">=3.6",
    author="",
    author_email="",
    description="",
    long_description="",
    long_description_content_type="text/x-rst",
    url="",
    project_urls={
        "Bug Tracker": "https://github.com/xxx/xxx/issues",
        "Documentation": "https://xxx.readthedocs.io",
    },
    license="GPL",
    classifiers=[
        "Development Status :: 3 - Alpha",
        "Environment :: Console",
        "Intended Audience :: Developers",
        "License :: OSI Approved :: GNU General Public License v3 or later (GPLv3+)",
        "Operating System :: POSIX :: Linux",
        "Programming Language :: Python :: 3",
        "Topic :: Software Development :: Debuggers",
    ],
)

```




## build

```
python3 setup.py build
```

## install

```
python3 setup.py install
```

等价于

```
python3 setup.py build && python3 setup.py install
```


```
running install
running bdist_egg
running egg_info
running install_lib
running build_py
running build_ext
```


## develop

```
python3 setup.py develop
```

* 如果是开发阶段，该命令不会真正的安装包，而是在系统环境中创建一个软链接指向包实际所在目录。 这样在修改包之后不用再安装就能生效，便于调试



## sdist

```
python3 setup.py sdist
```

* 支持指定压缩格式。在类 Unix 平台上，将创建后缀名默认为.tar.gz分发包，而在Windows上默认为 .zip 文件

```
python3 setup.py sdist --formats=gztar
```

* 执行后，文件夹下多了dist文件夹（包含压缩源码的分发包）和egg-info文件夹（中间临时配置信息）


## bdist

* python目前主流的二进制包格式是wheel（.whl后缀），它的前身是egg。
* wheel本质也还是一个压缩包，可以像像zip一样解压缩。
* 与源码包相比，二进制包的特点是不用再编译，也就是安装更快！
* 在使用wheel之前，需要先安装wheel ```pip3 install wheel```



## bdist_rpm

```
python3 setup.py bdist_rpm
```

* 生成rpm包。架构无关


## bdist_wininst

```
python3 setup.py bdist_wininst
```

* 生成windows下的包，exe格式


## bdist_dumb

```
python3 setup.py bdist_dumb
```

* 创建压缩包	tar,gztar,zip; windows默认zip，Unix默认gztar









## 参考

* <https://zhuanlan.zhihu.com/p/460233022>




---
