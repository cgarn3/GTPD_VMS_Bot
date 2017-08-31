# GTPD_VMS_Bot

This bot is implemented using Angular2 with Typescript. Refer [here](https://angular.io/docs/ts/latest/) for Angular2 documentation.

All the UI components are PrimeNG components. Refer [here](https://www.primefaces.org/primeng/#/) for PrimeNG documentation.

I also recommend using Visual Studio Code which can be downloaded [here](https://code.visualstudio.com/).

## How to Run:

Simply run `npm start` in the directory of this repo on your local machine. **If this is your first time running this project, please refer to the 'Onet-time Setup' directions below.**

`npm start` spins up a lite server that will open the app in your browser at localhost. The server watches for changes, so if any changes are made in the code, it will detect the changes and automatically refresh the page in the browser to reflect the changes.

**One-time Setup:**

1. Make sure node and npm are installed which can be found [here](https://docs.npmjs.com/getting-started/installing-node).

2. Clone this repo. 
    ```
    git clone https://github.gatech.edu/cgarn3/GTPD_VMS_Bot.git GTPD
    ```

3. Install the npm packages. 
    ```
    cd GTPD
    npm install
    ```
    **npm install fails in Bash for Windows which does not support networking to servers as of January, 2017.**

4. Start the app.
    ```
    npm start
    ```
    **npm start fails in Bash for Windows which does not support networking to servers as of January, 2017.**


## Background:

The Georgia Tech Police Department (GTPD) Video System Maintenance Bot's purpose is to troubleshoot any malfunctioning camera and generate a service request that gets sent to the appropriate camera vendor, so they can fix the issue. There are over 1700 security cameras on campus that currently rely on dispatchers or building managers to identify faulty cameras during monthly inspections. This often leads to delays and other inefficiency issues for GTPD which hinders them from keeping the campus as safe as possible. Moreover, there is additional time required to further identify the problem that lies within each of the malfunctioning camera and to contact the appropriate vendor. By developing this bot, it will reduce the time needed to manually complete all the necessary steps to bring a faulty camera back to normal operation.

The primary user of this product will be the IT employees of GTPD who are responsible for supervising the condition of the security cameras. Our product will be able to be run at specified times (i.e. daily, weekly, etc.) or manually at any time. After the bot is run, it will check each individual camera for maintenance issues. Whenever a malfunctioning camera is found, the bot will then attempt to do basic troubleshooting to try and identify the specific problem (i.e. ping tests for connectivity, etc.). Once complete, two separate reports will be generated: 1) a list of faulty cameras successfully troubleshot which will have generated service requests and 2) a list of faulty cameras unsuccessfully troubleshot which will not have generated service requests. The user can then examine the service requests the bot was able to generate as well as create service requests for the cameras the bot was unable to troubleshoot. The user will also have access to previous results from the bot running so that the user can ensure faulty cameras eventually get serviced. Our product will decrease the amount of time dedicated to tedious and repeated work as well as the amount of time that faulty cameras remain inactive.
