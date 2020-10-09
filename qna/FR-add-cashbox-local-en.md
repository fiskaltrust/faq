## Question
How to create the product ChaîneLocale?

## Metadata tags

lang-de, lang-at, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer

![ChaîneLocale](../images/FR/product_ChaineLocale.png)
The ChaîneLocale product allows the use of fiskaltrust.middleware on a POS system with a local installation. This product is free of charge and can be created at any time via the [fiskaltrust.Portal](https://portal.fiskaltrust.fr/). 
Several requirements must be fulfilled.

### Requirements

Log on to the [fiskaltrust.Portal](https://portal.fiskaltrust.fr/) as a PosDealer.

#### Activate cash register operator (PosOperator)

Open the menu _PosOperator_ and then click on the overview page. Next click on the magnifying glass in the first widget.

![Overview PosOperator](../images/FR/step_by_step_chainelocale_001.jpg)

Click on the matching PosOperator name in the first column to activate the account.

![List of PosOperators](../images/FR/step_by_step_chainelocale_002.jpg)

#### Enter SIREN and company name

First, a valid SIREN must be entered and checked in the company's master data. To do this, activate the master data of the company.

![Enter SIREN and company name](../images/FR/step_by_step_chainelocale_003.jpg)

Enter the company name as it appears in the commercial register at **1**. At **2** enter the SIREN of the company. (In sandbox mode, any 9-digit number can be used, for example 987654321). Then click on the check button **3** to check the SIREN against the commercial register. Save the data with the button at the end of the window.

#### Register outlet and SIRET

Click on _Outlets_ at the end of the company menu to display the list of branches.

![List of outlets](../images/FR/step_by_step_chainelocale_004.jpg)

The first branch is always the company headquarters, all others can be added. Open the corresponding branch or create a new one.

![SIRET](../images/FR/step_by_step_chainelocale_005.jpg)

In the window please enter the address **1** of the branch office and then in the field _Location Id_ the SIRET of the branch office **2**. (In sandbox mode, any 14-digit number can be used, for example 98765432100012. However, the first 9 digits must correspond to the SIREN used). Now check the Siret with the button on the right side **3** and save the data with the button at the bottom of the window.

### Creating a signature creation unit (SCU)

The signature creation device is the basis for the security and inalterability of the data. Once created, it cannot be deleted. It is a basic component of the configuration of the fiskaltrust.Middleware. Open the window for the SCUs in the _Configuration_ menu.

![show SCUs](../images/FR/step_by_step_chainelocale_006.jpg)

Click on the button _Create_ to create a new SCU. You only need one signature creation unit per outlet. One SCU can be used for several CashBoxes.

![add SCU](../images/FR/step_by_step_chainelocale_007.jpg)

Give the SCU a descriptive name **1**, and then select the **2** outlet for this signature creation unit.
Press the button at the bottom of the window to save the entries.

### Create a Queue

The queue is the storage location of all documents of a outlet. It can be created and managed in the _Configuration_ menu.

![Show Queues](../images/FR/step_by_step_chainelocale_008.jpg)

Create a new queue with the button _New_. You need at least one queue per outlet. One queue can manage up to 10 POS systems. For this purpose, the queue must be accessible from every single POS system in the network.

![Add Queue](../images/FR/step_by_step_chainelocale_009.jpg)

Complete the values in this window. The description **1** is only for your convenience to identify the queue. The version number **2** must be selected correctly to comply with the law. The identification of the CashBox **3** must be unique around the account and serves as internal identification. Before saving, please select the appropriate outlet.

**When selecting the outlet, always make sure to use the correct one and always the same one. This cannot *not* be changed afterwards!

![Add Queue](../images/FR/step_by_step_chainelocale_010.jpg)

Save this configuration and add an http URL in the following window without changing any of the other values. Save the configuration.

### Assigning the SCU to the queue

To ensure the security of the documents stored in the queue, the signature creation device must be connected to the queue.

![Connect SCU](../images/FR/step_by_step_chainelocale_011.jpg)

Find the recently created queue in the list. There are four configuration buttons on the right side. Click the first one (the square with an arrow).

![Connect SCU](../images/FR/step_by_step_chainelocale_012.jpg)

Select the SCU you created in the first step and click _Save and close_.

**Be careful with this step, the SCU for this queue cannot be changed afterwards!

### Setup CashBox

To connect the POS system with the fiskaltrust.Middleware you need the virtual configuration container _CashBox_.

![Create CashBox](../images/FR/step_by_step_chainelocale_013.jpg)

In the CashBox command of the configuration menu, you must click the _Add_ button.

![Create CashBox](../images/FR/step_by_step_chainelocale_014.jpg)

Enter a _description_ **1** and select the same branch **2** as in the previous steps again. After clicking on _Save_ you will find a new CashBox in the list.

![Create CashBox](../images/FR/step_by_step_chainelocale_015.jpg)

Click on the button with the hand symbol.

![Create CashBox](../images/FR/step_by_step_chainelocale_016.jpg)

Now drag the recently created queue from right to left. Check that the correct branch is selected and click on _Save_.

### Rebuild configuration

After each change to the CashBox, you must put together a new one.

![Load Launcher](../images/FR/step_by_step_chainelocale_017.jpg)

Click on the *Rebuild Configuration* button (circular arrows) **1** in the CashBox line.
Now you can download one of the three launchers **2** and install the fiskaltrust.Middleware on your local POS system.
