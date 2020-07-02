## Question
How to create a local CashBox?

## Metadata tags
lang-en, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
To create a CashBox, certain conditions must be met beforehand:

* A valid SIREN number must be entered and checked in the basic data of the company.
* A valid branch must be registered. For this, the address of the branch and its SIRET number must be entered and verified.

Once these two conditions are met, a CashBox can be created in following 5 steps:

**Step One:**<br>Create a Signature Creation Unit (SCU) in the Configuration menu. Click on the “Create” button to start. Add a description of the SCU (for your reference) and select the correct outlet. Then click on the “Save” button to conclude the creation of the SCU.

**Step Two:**<br>Create a queue for your Outlet. Go to the Configuration menu and open the subcategory “Queue”. By clicking on the button “Create new Queue” you start the creation. Add a description of the Queue (for your reference) and accept the preselected SQLite-Package. The Package version should be the latest 1.2 package (without the “-dev” suffix). The “Location Id” must be the same as the one selected in the previous step.  Add a unique CashBox identification.

Save this configuration and in the following window click the “HTTP” button to add an http-URL. Do not change any of the other values. Finally, save the configuration.

**Step Three:**<br>Return to the Configuration menu and open the subcategory “Queue”. Find the recently created Queue in the list and on the far right hand side are four configuration buttons. Click on the first one (the square with the arrow in it). Choose the SCU that you created in the first step and click on “Save and close”.

Be careful while executing this step, the SCU will be fixed to this Queue and cannot be changed in the future.

**Step Four:**<br>Return to the Configuration menu and open the subcategory “CashBox”. In the CashBox of the configuration menu you must click on the “+ Add” button. Enter a description and select the same outlet selected in the previous steps. After clicking on save, you will find a new CashBox in the list. Click on the button with the pointing hand on it. Now drag and drop the recently created queue from the column on the right side to the column on the left side. Verify that it is the correct outlet that is selected and click on save.

**Step Five:**<br>Click on the rebuild configuration button (refresh circle arrows) in the row of the relevant CashBox.

Now you can download one of the three launchers and install the fiskaltrust.Middleware on your local machine.
