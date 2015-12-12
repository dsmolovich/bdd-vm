# Behat + Mink + Selenium2 under the vagrant setup.

## Prerequisites:
- Virtualbox https://www.virtualbox.org/
- Vagrant https://www.vagrantup.com/
- X11 server (if you want to observe the testing process in a forwarded window)
-- For Mac: XQuartz http://www.xquartz.org/
-- For Windows: XMing http://sourceforge.net/projects/xming/
-- For Linux: most likely you already have it installed

## Installation:
1. Clone the repository
2. ```vagrant up```
3. Wait for everything to be installed. It takes some time.

## Run tests with headless browser:
1. ```vagrant ssh```
2. ```pkill java```
3. ```selenium.headless.start```
4. ```tail -f /tmp/selenium.log``` and wait for line '... INFO - Selenium Server is up and running' to appear
5. ```behat features/examples/search.feature```

## Run tests observing the process in forwarded browser window:
1. ```vagrant ssh```
2. ```pkill java```
3. ```selenium.start```
4. ```tail -f /tmp/selenium.log``` and wait for line '... INFO - Selenium Server is up and running' to appear
5. ```behat features/examples/search.feature```

