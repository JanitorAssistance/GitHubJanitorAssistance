.. default-role:: code


Browser: Firefox Operation System: Windows 8.1

Markos occupation: Software engineering student at JAMK. Age: 35

Marko is an older student in JAMK, learning software testing with robotframework GUI RIDE and it's extension library Selenium2Library.

Primary Actor: Marko

Roles: Common Users

============
Idea behind
============

Marko gets an assignment from Niko at JAMK. The idea is try to configure the RobotFramework to run a successful test suite and build a story around it.


============
Scenario 1 
============

Marko has setted up RobotFramework in RIDE and is ready to run the tests, but decides to check the settings manually, before running the tests. He has also commented the tests for easier readability.

.. code:: robotframework

            *** Settings ***
            Documentation     *Content overview*
            ...
            ...               This testsuite checks the user login and logout capabilities of the _python.org_ website.
            Suite Setup       Open Browser    ${SITE URL}
            Suite Teardown    Close Browser
            Force Tags        python.org
            Library           Selenium2Library
            Resource          example_testsuite_resource_file.txt

=================
Scenario 1 Tests
=================

Marko opens his computer and and starts a web browser and goes to the webpage where Python.org resides.

.. code:: robotframework

            *** Test Cases ***
            Test Navigate To User Sign In Page
                [Documentation]    *Verifies navigation to the sign in page*
                [Tags]    navigation
                Navigate To User Sign In Page
                Page Should Contain    Username:
                Page Should Contain    Password:
                Page Should Contain Button    ${FORM BUTTON LOCATOR}
                Location Should Be    ${SIGN IN URL}

Marko selects login option from mainpage and types in the obtained test username and password. The login is successful and Marko can explore the python.org as a registered user. 			
				
				
.. code:: robotframework

           *** Test Cases ***
            Test Sign In User
                [Documentation]    *Verifies that after login the user is directed to the main page*
                [Tags]    login
                Sign In User
                Page Should Contain    Your account
                Location Should Be    ${SITE URL}/

After wondering around a while, he remembers that this is just an test use for the settings and tries to remember what he needs do next. Accidentally he closes the web browser and wonders how the test handles the closing. He decides to open the browser again and go to the python.org. He notices that the login provided has successfully survided the closing and browsing can continue as usuall. After a while he logs out and gets redirected to mainpage.  				
				
.. code:: robotframework

           *** Test Cases ***
            Test Sign Out User
                [Documentation]    *Verifies that after logout the user is directed to the main page*
                [Tags]    logout
                [Setup]    Get New Browser
                Sign Out User
                Page Should Contain    Sign In
                Location Should Be    ${SITE URL}/

Happy that the test plan is successful, Marko closes the web browser and forms a documentation of the example and returns it to Niko, with a screenshot of the PASSed tests in RIDE.

=================
Includes for Niko:
=================

Image at: https://github.com/JanitorAssistance/GitHubJanitorAssistance/blob/master/RIDE-S2L-Example-for-JAMK/RIDE%20test%20PASSes.JPG?raw=true)

Resources at: https://github.com/JanitorAssistance/GitHubJanitorAssistance/blob/master/RIDE-S2L-Example-for-JAMK/Testsuite_resource_file.txt
