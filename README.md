# Config environment

setup scripts

## Config java

- Download jdk

`curl -LO 'http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz' -H 'Cookie: oraclelicense=accept-securebackup-cookie'`

- Extract and set java home

````
sudo mkdir /usr/lib/jvm
sudo tar zxvf ./jdk-7u79-linux-x64.tar.gz  -C /usr/lib/jvm
cd /usr/lib/jvm
sudo mv jdk1.7.0_79/ java-sun

sed -i '$ a\'"export JAVA_HOME=/usr/lib/jvm/java-sun" ~/.bashrc
sed -i '$ a\'"export JRE_HOME=\${JAVA_HOME}/jre " ~/.bashrc
sed -i '$ a\'"export PATH=\${JAVA_HOME}/bin:\$PATH" ~/.bashrc

source ~/.bashrc

echo "Update alternatives"
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-sun/bin/java 300
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/java-sun/bin/javac 300
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/java-sun/bin/jar 300
sudo update-alternatives --install /usr/bin/javah javah /usr/lib/jvm/java-sun/bin/javah 300
sudo update-alternatives --install /usr/bin/javap javap /usr/lib/jvm/java-sun/bin/javap 300

java -version
````

