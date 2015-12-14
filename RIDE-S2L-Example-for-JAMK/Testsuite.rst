.. default-role:: code

============
Scenario 1
============

Browser: Firefox Operation System: Windows 8.1

Markos occupation: Software engineering student at JAMK. Age: 35

Marko is an older student in JAMK, learning software testing with robotframework GUI RIDE and it's extension library Selenium2Library.

Primary Actor: Marko

Roles: Common Users


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

.. code:: robotframework

           *** Test Cases ***
            Test Sign In User
                [Documentation]    *Verifies that after login the user is directed to the main page*
                [Tags]    login
                Sign In User
                Page Should Contain    Your account
                Location Should Be    ${SITE URL}/

.. code:: robotframework

           *** Test Cases ***
            Test Sign Out User
                [Documentation]    *Verifies that after logout the user is directed to the main page*
                [Tags]    logout
                [Setup]    Get New Browser
                Sign Out User
                Page Should Contain    Sign In
                Location Should Be    ${SITE URL}/
