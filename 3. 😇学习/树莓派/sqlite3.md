sudo apt-get update
sudo apt-get install sqlite
sudo apt-get install sqlite3

安装出错`依赖: libsqlite3-0 (= 3.8.7.1-1+deb8u4) 但是 3.16.2-5+deb9u1 正要被安装`

sudo dpkg --purge --force-depends libsqlite3-0
sudo apt-get install libsqlite3-0
sudo apt-get install -f
sudo apt-get install libsqlite3-dev
sudo apt-get install sqlite3

## npm install sqlite3
安装失败，把node自带的node-gyp替换掉

sudo npm cache clean -f
sudo npm install npm -g
sudo npm uninstall node-gyp -g
sudo npm install node-gyp -g // 失败
sudo  yarn add global node-gyp // 成功

sudo npm install sqlite3 // 依然失败
sudo yarn add sqlite3 // 成功