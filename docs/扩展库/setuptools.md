# setuptools

![20220408_154151_30](image/20220408_154151_30.png) 

## 相关链接

* <https://pypi.org/project/setuptools/7.0/>
* <https://setuptools.pypa.io/en/latest/userguide/index.html>


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
















---
