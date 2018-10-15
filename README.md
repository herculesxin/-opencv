在树莓派上安装opencv
第一步：
更新
sudo apt-get update 
sudo apt-get -y dist-upgrade

第二步：
配置SSH和实用程序
sudo apt-get install screen 
sudo apt-get install htop

第三步：
安装依赖
sudo apt-get install build-essential cmake pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
sudo apt-get install libgtk2.0-dev libgtk-3-dev
sudo apt-get install libatlas-base-dev gfortran

第四步：
安装python2.7 & 3
sudo apt-get install python2.7-dev 
sudo apt-get install python3-dev

第五步：
下载opencv的源
wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.1.ziphttps://github.com/opencv/opencv/archive/3.4.1.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.1.ziphttps://github.com/opencv/opencv_contrib/archive/3.4.1.zip
unzip opencv.zip
unzip opencv_contrib.zip


第六步：
安装pip和virtualenv
wget -O get-pip.py https ：// bootstrap 。pypa 。io / get - pip 。py  https ：// bootstrap 。pypa 。io / get - pip 。py  
sudo python get-pip.py 
sudo python3 get-pip.py

第七步：
安装虚拟环境
sudo pip install virtualenv virtualenvwrapper
修改〜/ .profile文件以包含以下行：
export WORKONHOME = $ HOME / .virtualenvs 
export VIRTUALENVWRAPPER_PYTHON = / usr / bin / python3 
source /usr/local/bin/virtualenvwrapper.sh
修改后像这样
＃〜/ .profile：由命令解释器为登录shell执行。
＃如果〜/ .bash_profile或〜/ .bash_login 
＃存在，则bash（1）不读取此文件。
＃例如，参见/ usr / share / doc / bash / examples / startup-files。
＃文件位于bash-doc包中。
＃在/ etc / profile中设置默认的umask; 要
为ssh登录设置umask ＃，请安装并配置libpam-umask包。
#umask 022 
＃如果运行bash 
if [-n“$ BASH_VERSION”]; 然后
    #include .bashrc如果它存在，
    如果[-f“$ HOME / .bashrc”]; 然后
        。“$ HOME / .bashrc” 
    fi 
fi 
＃设置PATH，因此它包含用户的私有bin（如果存在）
if [-d“$ HOME / bin”]; 然后
    PATH =“$ HOME / bin：$ PATH” 
fi 
＃virtualenv和virtualenvwrapper settings 
export WORKON_HOME = $ HOME / .virtualenvs 
export VIRTUALENVWRAPPER_PYTHON = / usr / bin / python3 
source /usr/local/bin/virtualenvwrapper.sh


第八步：
激活更改：
source ~/.profile

第九步：
创建虚拟环境
mkvirtualenv cv -p python3


第十步：
安装Numpy，Scipy
sudo pip install numpy scipy

第十一步：
安装OpenCV
cd  /opencv-3.4.1 
mkdir build 
cd /build 

cmake -D CMAKE_BUILD_TYPE = RELEASE \ 
    -D CMAKE_INSTALL_PREFIX = / usr / local \ 
    -D INSTALL_PYTHON_EXAMPLES = ON \ 
    -D OPENCV_EXTRA_MODULES_PATH =〜/ opencv_contrib-3.4.1 / modules \ 
    - D BUILD_EXAMPLES = ON ..


第十二步：
使用你的4个cpu
make -j4



第十三步：
OpenCV成功编译后，继续安装：
sudo make install 
sudo ldconfig 
sudo apt-get update
重启系统

第十四步：
最后你可以测试
$ python3
Python 3.5.3 (default, Jan 19 2017, 14:11:04) 
[GCC 6.3.0 20170124] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import cv2
>>> cv2.__version__
'3.4.1'

或者
pkg-config --modversion opencv
