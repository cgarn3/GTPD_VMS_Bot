# GTPD_VMS_Bot

This application is an automated bot used to diagnose and troubleshoot malfunctioning security cameras for the Georgia Tech Police Department. More information can be found at the bottom in the 'Background' section.

Some things to note:
- This application is implemented using Angular2 with Typescript. Refer [here](https://angular.io/docs/ts/latest/) for Angular2 documentation.
- All the UI components are PrimeNG components. Refer [here](https://www.primefaces.org/primeng/#/) for PrimeNG documentation.
- This application leverages Python 3.
- Angular handles all its own URL routing. Flask just serves the "index.html" regardless of where the user navigates.

## How to Run locally:

**If this is your first time running this application, please refer to the 'Onet-time Setup' directions.**
**Otherwise, follow the instructions below.**

------------------------------------------------------------------------
**MacOS / Linux:**

1. Navigate to this repository on your local machine
2. Start the server:
    ```
    make run
    ```

3. Navigate to [localhost:8080](http://localhost:8080/) in your browser

**Windows:**

1. Navigate to this repository on your local machine
2. Start the server:
    ```
    python main.py
    ```

3. Navigate to [localhost:8080](http://localhost:8080/) in your browser

------------------------------------------------------------------------

**One-time Setup:**

1. Clone this repo:
    ```
    git clone https://github.gatech.edu/cgarn3/GTPD_VMS_Bot.git GTPD
    ```

2. Download [Python 3](https://www.python.org/downloads/) if you do not already have it

3. Install `node` and `npm` which can be found [here](https://docs.npmjs.com/getting-started/installing-node)

4. Install the necessary typescript modules:    
    ```
    npm install -g typescript
    ```

5. Install [pip](https://pip.pypa.io/en/stable/installing/) if you do not already have it

6.  Follow the instructions for your OS

**MacOS / Linux:**

1. Update pip:
    ```
    pip install -U pip
    ```

2. Install the required dependencies:
    ```
    make install
    ```

3. Start the server:
    ```
    make run
    ```

4. Navigate to [localhost:8080](http://localhost:8080/) in your browser

**Windows:**

1. Update pip:
    ```
    python -m pip install -U pip
    ```

2. Manually install the required dependencies:
    ```
    python -m pip install -r requirements.txt
    npm --prefix ./templates install ./templates
    tsc -p ./templates
    ```

3. Start the server:
    ```
    python main.py
    ```

4. Navigate to [localhost:8080](http://localhost:8080/) in your browser

------------------------------------------------------------------------

## Background:

The Georgia Tech Police Department (GTPD) Video System Maintenance Bot's purpose is to troubleshoot any malfunctioning camera and generate a service request that gets sent to the appropriate camera vendor, so they can fix the issue. There are over 1700 security cameras on campus that currently rely on dispatchers or building managers to identify faulty cameras during monthly inspections. This often leads to delays and other inefficiency issues for GTPD which hinders them from keeping the campus as safe as possible. Moreover, there is additional time required to further identify the problem that lies within each of the malfunctioning camera and to contact the appropriate vendor. By developing this bot, it will reduce the time needed to manually complete all the necessary steps to bring a faulty camera back to normal operation.

The primary user of this product will be the IT employees of GTPD who are responsible for supervising the condition of the security cameras. Our product will be able to be run at specified times (i.e. daily, weekly, etc.) or manually at any time. After the bot is run, it will check each individual camera for maintenance issues. Whenever a malfunctioning camera is found, the bot will then attempt to do basic troubleshooting to try and identify the specific problem (i.e. ping tests for connectivity, etc.). Once complete, two separate reports will be generated: 1) a list of faulty cameras successfully troubleshot which will have generated service requests and 2) a list of faulty cameras unsuccessfully troubleshot which will not have generated service requests. The user can then examine the service requests the bot was able to generate as well as create service requests for the cameras the bot was unable to troubleshoot. The user will also have access to previous results from the bot running so that the user can ensure faulty cameras eventually get serviced. Our product will decrease the amount of time dedicated to tedious and repeated work as well as the amount of time that faulty cameras remain inactive.
