# InsightAgent: New relic
Agent Type: New relic

Platform: Linux

InsightFinder agent can be used to monitor system performance metrics on bare metal machines or virtual machines.

##### Instructions to register a project in Insightfinder.com
- Go to [insightfinder.com](https://insightfinder.com/)
- Sign in with the user credentials or sign up for a new account.
- Go to Settings and Register for a project under "Insight Agent" tab.
- Give a project name, select Project Type as "Private Cloud".
- View your account information by clicking on your user id at the top right corner of the webpage. Note the license key number.

##### Pre-requisites:
Python 2.7.

Python 2.7 must be installed in order to launch deployInsightAgent.sh. For Debian and Ubuntu, the following command will ensure that the required dependencies are present
```
sudo apt-get upgrade
sudo apt-get install build-essential libssl-dev libffi-dev python-dev wget
```
For Fedora and RHEL-derivatives
```
sudo yum update
sudo yum install gcc libffi-devel python-devel openssl-devel wget
```

##### To install agent on the machine
1) Use the following command to download the insightfinder agent code.
```
wget --no-check-certificate https://github.com/insightfinder/InsightAgent/archive/master.tar.gz -O insightagent.tar.gz
```
Untar using this command.
```
tar -xvf insightagent.tar.gz
```

2) In InsightAgent-master directory, make changes to the config file.
```
newrelic/newrelic.cfg
```
Update the API_KEY. This key can be obtained from new relic website by clicking on Account Setting > API Keys > Show key

Update the hostapp section to include the host names and corresponding applications which you want to monitor. You can find the hostnames and corresponding appnames on the New relic dashboard.If you want to monitor multiple hosts and app write (hostname1:appname1),(hostname2:appname2),..... ,(hostnameN:appnameN)

3) run the following commands to install and use python virtual environment for insightfinder agent:
```
./deployment/checkpackages.sh
```
```
source pyenv/bin/activate
```

4) Run the below command to install agent.
```
./deployment/install.sh -i PROJECT_NAME -u USER_NAME -k LICENSE_KEY -s SAMPLING_INTERVAL_MINUTE -r REPORTING_INTERVAL_MINUTE -t AGENT_TYPE
```
After using the agent, use command "deactivate" to get out of python virtual environment.

