# GTPD_VMS_Bot

This application is an automated bot used to diagnose and troubleshoot malfunctioning security cameras for the Georgia Tech Police Department. More information can be found at the bottom in the 'Background Information' section.

## Table of Contents
- [Release Notes](#releaseNotes)

- [Install Guide](#installGuide)

- [Background Information](#background)

<a name="releaseNotes"/>

## Release Notes - GTPD_VMS_Bot v1.0
- New Features
    - Home page with quick view of latest camera diagnostics
    - Feature to run the bot on demand
    - Feature to schedule the bot to run on a fixed recurring or one time basis
    - Introduced a view to see the history of the bot's diagnostic results
    - Can now update the cameras to test via uploading an excel spreadsheet
    - User can add/update/modify usernames and passwords used to SSH into the cameras
- Bug Fixes
    - N/A - this is the first release
- Known Bugs
    - The bot's scheduled runtime cannot be changed without first selecting a date within the dropdown calendar
    - After adding a username and password, you cannot delete it until you refresh the page
    - After uploading a new camera spreadsheet, you have to refresh the page to see the updated camera info in the table
    - When you select a previous run to view, the 'Last Run:' variable next to the 'Run Bot' button shows the runtime of the previous run being view rather than the latest run time

<a name="installGuide"/>


## Install Guide
- Pre-requisites
    - The application is designed for a Red Hat Linux server

- Dependencies
    - [Python 2.7](https://www.python.org/download/releases/2.7/)
    - [pip](https://pip.pypa.io/en/stable/installing/)
    - [Node and NPM](https://docs.npmjs.com/getting-started/installing-node)
    - MySQL
    - All the UI components are PrimeNG components. Refer [here](https://www.primefaces.org/primeng/#/) for PrimeNG documentation.
    - This application is implemented using Angular2 with Typescript. Refer [here](https://angular.io/docs/ts/latest/) for Angular2 documentation.

- Download Instructions
    - Clone this repo
    ```
    git clone https://github.gatech.edu/cgarn3/GTPD_VMS_Bot.git GTPD
    ```

- Build Instructions
    - Setup MySQL database:
        1. In the directory that the application folder is in, download [MySQL](https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm)
        
        2. Add the downloaded MySQL repo
        ```
        sudo yum install mysql57-community-release-el7-11.noarch.rpm
        ```
        
        3. Install MySQL
        ```
        sudo yum install mysql-community-server
        ```
        
        4. Start the MySQL server
        ```
        sudo service mysqld start
        ```
        
        5. Setup the database by executing the SQL queries stored in
        ```
        GTPD/sql_queries
        ```
        
        6. Update the database configurations in
        ```
        GTPD/config.py
        ```

- Installation
    - In the root directory of the application folder, install Typescript
    ```
    npm install -g typescript
    ```
    
    - Update pip:
        ```
        pip install -U pip
        ```
    - Install the required dependencies:
        ```
        make install
        ```

- How to Run:
    - Start the server:
        ```
        make run
        ```
    - Navigate to [https://localhost:8080](https://localhost:8080/) in your browser
    
- Troubleshooting
    - If you are using windows, you cannot use the 'make' commands.
        - Manually install the required dependencies
        ```
        python -m pip install -r requirements.txt
        npm --prefix ./templates install ./templates
        tsc -p ./templates
        ```

        - Start the server by running
        ```
        python main.py
        ```
        
        - Then, navigate to [https://localhost:8080](https://localhost:8080/) in your browser

<a name="background"/>

## Background Information

The Georgia Tech Police Department (GTPD) Video System Maintenance Bot's purpose is to troubleshoot any malfunctioning camera and generate a service request that gets sent to the appropriate camera vendor, so they can fix the issue. There are 1700+ security cameras on campus that currently rely on dispatchers or building managers to identify faulty cameras during monthly inspections. This often leads to delays and other inefficiency issues for GTPD which hinders them from keeping the campus as safe as possible. Moreover, there is additional time required to further identify the problem that lies within each of the malfunctioning camera and to contact the appropriate vendor. By developing this bot, it will reduce the time needed to manually complete all the necessary steps to bring a faulty camera back to normal operation.

The primary user of this product will be the IT employees of GTPD who are responsible for supervising the condition of the security cameras. Our product will be able to be run at specified times (i.e. daily, weekly, etc.) or manually at any time. After the bot is run, it will check each individual camera for maintenance issues. Whenever a malfunctioning camera is found, the bot will then attempt to do basic troubleshooting to try and identify the specific problem (i.e. ping tests for connectivity, etc.). Once complete, two separate reports will be generated: 1) a list of faulty cameras successfully troubleshot which will have generated service requests and 2) a list of faulty cameras unsuccessfully troubleshot which will not have generated service requests. The user can then examine the service requests the bot was able to generate as well as create service requests for the cameras the bot was unable to troubleshoot. The user will also have access to previous results from the bot running so that the user can ensure faulty cameras eventually get serviced. Our product will decrease the amount of time dedicated to tedious and repeated work as well as the amount of time that faulty cameras remain inactive.
