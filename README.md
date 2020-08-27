# Automating Docker container deployment with Jenkins :whale: 

> Objective: Full automation of deployment pipeline 

Jenkins is a Continuous Integration automation control software that allows you to automate repetitive parts of the software development process

## Part I Installing Java8 and Jenkins
1. Install Jenkins on MacOS using Homebrew package manager :beers: If homebrew already installed (run in Termainl `brew -v` to check), skip to the next step 
```bash
/usr/bin/ruby -e /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Check if Homebrew requires any recommendations:
```bash
brew doctor
```

3. Before installing Jenkins, we need to install Java8
```bash
brew cask install java8
```
**Troubleshooting error**:
```bash
Cask 'java8' is unavailable: No Cask with this name exists.
java --version
java 14.0.1 2020-04-14
Java(TM) SE Runtime Environment (build 14.0.1+7)
Java HotSpot(TM) 64-Bit Server VM (build 14.0.1+7, mixed mode, sharing)
``` 

Jenkins requires Java8. Click [here](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) to install.

Check all installed java version
```bash
/usr/libexec/java_home -V
```
**which returns**
```bash
Matching Java Virtual Machines (2):
    14.0.1, x86_64:	"Java SE 14.0.1"	/Library/Java/JavaVirtualMachines/jdk-14.0.1.jdk/Contents/Home
    1.8.0_251, x86_64:	"Java SE 8"	/Library/Java/JavaVirtualMachines/jdk1.8.0_251.jdk/Contents/Home
```

Pick `1.8.0_251, x86_64` to set as the default then:
```bash
export JAVA_HOME=`/usr/libexec/java_home -v 1.8.0_251, x86_64`
```

When you run java -version you will see:
```bash
java version "1.8.0_251"
```

4. To make the Jenkins web interface accessible from anywhere, not just local machine, open up the config file:
```bash
sudo nano /usr/local/opt/jenkins-lts/homebrew.mxcl.jenkins-lts.plist
```

5. Find this line:
```bash
<string>--httpListenAddress=127.0.0.1</string>
```

6. Change it to:
```bash
<string>--httpListenAddress=0.0.0.0</string>
```
To exit out of nano, press `Ctrl+X`, hit `Y` to save Changes, hit `Enter`

7. Start or restart Jenkins
```bash
brew services start jenkins-lts
brew services restart jenkins-lts
```

8. Open the browser and type in the following:
```bash
http://localhost:8080/
```

