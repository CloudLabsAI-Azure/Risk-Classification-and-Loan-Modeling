# Risk-Classification-and-Loan-Modeling

![MSUS Solution Accelerator](https://github.com/MSUSAzureAccelerators/Risk-Classification-and-Loan-Modeling-Accelerator/blob/main/images/MSUS%20Solution%20Accelerator%20Banner%20Two_981.png)

# Risk Classification and Loan Modeling

The objective of the Risk Classification with Loan Modeling accelerator is to predict how much loan amount will be approved by the SBA & their registered lenders when a business applies for a loan through the SBA. 
  
The Small Business Administration (SBA) was founded in 1953 to assist small businesses and entrepreneurs in obtaining loans. Small businesses have been the primary source of employment in the United States-helping with job creation which reduces unemployment. Small business growth also promotes economic growth. One of the ways the SBA helps small businesses is by guaranteeing bank loans. This guarantee reduces the risk to banks and encourages them to lend to small businesses. If the loan defaults, the SBA covers the amount guaranteed, and the bank suffers a loss for the remaining balance.


## Exercise 1 : View the PowerBI report Dashboard

1. In the Desktop click on the **Power BI Desktop** icon.

    ![Risk Classification](./images/1.png)  
    
2. Click on the **X** symbol to close Get Started page.

    ![Risk Classification](./images/2.png)  
    
3. Click on the File option.

    ![Risk Classification](./images/3.png)
    
4. In the **Open reports(1)** section click on the **Browse report(2)**.

    ![Risk Classification](./images/4.png)  
    
5. Move to the location **C:\LabFiles(2)** , select the **RCLM-file(3)** and click **Open(4)**.

    ![Risk Classification](./images/5.png)
 
 6. On **RCLM_file** tab click on **Load**.

    ![Risk Classification](./images/6.png)
    
7. On **Refresh** Page click on **Close**.
  
    ![Risk Classification](./images/7.png)
    
8. Click on **Down Arrow in the Transform Data(1)** and select **Data Source Setting(2)**

    ![Risk Classification](./images/8.png)
    
9. Click on **Change Source** on Data Source Setting page.

    ![Risk Classification](./images/9.png)

10. Type **sbadataDID(1)** and click **Ok(2)**.

     **Note**: Replace **DID** by the **Deployment ID** provided in the environment details

     ![Risk Classification](./images/10.png)

     **Note**: If the Account key is popup for the Authentication go to the Azure portal to the **sbadataDID** storage account and in the **Access keys** section select **key1**.
     
     ![Risk Classification](./images/11.png)

11. click **Close**.

    ![Risk Classification](./images/12.png)
    
12. Click on **Apply Changes** wait untill the load is **complete** and click on close.

      **Note**: Ignore if there is any errors

     ![Risk Classification](./images/13.png)
    
13. Review the Dashboard.

     ![Risk Classification](./images/14.png)


## Exercise 2 : Running the machine learning pipelines

### Task 1: Predict Loan Risk via Classification Model

1. Go to the Azure Portal and search for the **Azure Machine Learning** and select it.
 
    ![Risk Classification](./images/15.png)

2. Select the **loanmodelDID** in the under Azure Machine Learning.

    ![Risk Classification](./images/17.png)

3. Click on the **Launch Studio**

     ![Risk Classification](./images/18.png)

4. In the Azure Machine Learning Studio, click on the **Designer(1)** and Click on **Create the pipline using classic pre-built modules(2)**.

     ![Risk Classification](./images/19.png)

5. In the designer page click on the **settings**.
    
    ![Risk Classification](./images/20.png)

6. For **Select Compute type**: **Container Instance(1)**, for **Select Azure ML compute instance** : **loanmodel(2)** and click on **Save(3)**.

    ![Risk Classification](./images/21.png)
    
7. Under the **Data** Section Drag and Drop **SBADATA** to the worspace.

    ![Risk Classification](./images/22.png)

8. Under the **Component** Section Search for **Select Columns in Dataset** and Drag and Drop at Workspace region.

    ![Risk Classification](./images/23.png)

9. Connect **SBADATA(1)** output to input of **Select Columns in Dataset(2)**.

    ![Risk Classification](./images/24.png)

10. Double click on the **Select Columns in Dataset** icon then under select columns click on **edit columns**.

     ![Risk Classification](./images/25.png)

11. Enter all the below coloumn names and click on **save**.
 (City,State,Bank,BankState,Term,NoEmp,NewExist,CreateJob,RetainedJob,FranchiseCode,UrbanRural,RevLineCr,LowDoc,DisbursementGross,GrAppv,SBA_Appv,IndustryCode,Risk)

     ![Risk Classification](./images/26.png)

12. Under the **Component** section search **Clean Missing Data** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/27.png)

13. Connect **select Columns in Dataset(1)** output to input of **Clean Missing Data(2)**.

     ![Risk Classification](./images/28.png)

14. Double click on the **Clean Missing Data** icon then under select columns click on **edit columns**.

     ![Risk Classification](./images/29.png)

15. Under **cloumns to be cleaned** page for **Include** selct **All Columns**.

     ![Risk Classification](./images/30.png)

16. Click on **Save**.

     ![Risk Classification](./images/31.png)

17. Select the **Remove entire row** for **Cleaning mode**.

     ![Risk Classification](./images/32.png)

18. Under the **Component** section search **Split Data** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/33.png)

19. Connect **Clean Missing Data(1)** left output to input of **Split Data(2)**.

     ![Risk Classification](./images/34.png)

20. Double click on the **Split Data** icon for **Fraction of rows in the first output dataset** change the value to **0.7**.

     ![Risk Classification](./images/35.png)

21. Under the **Component** section search **Multiclass logistic Regression** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/36.png)

22. Under the **Component** section search **Train Model** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/37.png)

23. Connect output of the **Multiclass logistic Regression(1)** to the left input of **Train Model(2)** and left output of the **Split Data(3)** to **Train Model(4)**

     ![Risk Classification](./images/38.png)

24. Double click on the **Train Model** icon then under Label columns click on **edit column**

     ![Risk Classification](./images/39.png)

25. Under the **Label Column** select **column names** and type **Risk** and click on **Save**.

     ![Risk Classification](./images/40.png)

26. Under the **Component** section search **Score Model** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/41.png)

27. Connect output of the **Train Model(1)** to the left input of **Score Model(2)** and Right output of the **Split Data(3)** to **score Model(4)**

     ![Risk Classification](./images/42.png)

28. Under the **Component** section search **Evaluate Model** and Drag and Drop at the workspace region.

     ![Risk Classification](./images/43.png)

29. Connect **Score Model(1)** left output to input of **Evaluate Model(2)**.

     ![Risk Classification](./images/44.png)

30. Click on **Submit**.

     ![Risk Classification](./images/45.png)

31. On **Setup Pipeline job** page select **Create new**, **New Experiment Name** : **SBA_Loan_Risk_Prediction** and click on **Submit**.

      ![Risk Classification](./images/46.png)

32. Wait untill the Pipline run is completed.

     ![Risk Classification](./images/47.png)

33. Right click on the **evaluate model**, click on the **preview data** and click on **Evaluate Results**.

     ![Risk Classification](./images/48.png)
     
34. Verify the evaluation results.

     ![Risk Classification](./images/49.png)


### Task 2: create regression model to predict SBA approval amount

1. Go to the **Jobs** section and click on the latest succeeded run for SBA Loan Prediction.

    ![Risk Classification](./images/50.png)

2. Click on **Clone**.

    ![Risk Classification](./images/51.png)

3. Double click on the **Select Columns in Dataset** icon then under select columns click on **edit columns**.

     ![Risk Classification](./images/52.png)

4. Remove **Risk** and click on **Save**.

    ![Risk Classification](./images/53.png)

5. Right click on the **Multiclass Logistic Regression** and click on **Delete**.

    ![Risk Classification](./images/54.png)

6. Under the **Component** section search **Linear Regression** and Drag and Drop at the workspace region.

    ![Risk Classification](./images/55.png)

7. Connect **Linear Regression(1)** output to input of **Train Model(2)**.

    ![Risk Classification](./images/56.png)
  
8. Double click on the **Train Model** icon then under Label columns click on **edit column**.

    ![Risk Classification](./images/57.png)

9. Add **SBA_Appv** and click on **save**.

    ![Risk Classification](./images/58.png)

10. Click on **Submit**.

     ![Risk Classification](./images/45.png)

11. On **Setup Pipeline job** page select **Create new**, **New Experiment Name** : **SBA_Loan_Approve_Amount_Prediction** and click on **Submit**.

     ![Risk Classification](./images/59.png)

12. Right click on the **evaluate model**, click on the **preview data** and click on **Evaluate Results**.

     ![Risk Classification](./images/48.png)

13. Verify the evaluation results.

     ![Risk Classification](./images/60.png)


## Exercise 3 : Deploy the Batch Processing ML Model

1. Go to the **LoanmodelDID** synapse workspace in the Azure Portal and click on **open**.

    ![Risk Classification](./images/64.png)

2. In the Synapse workspace, click on **Integrate(1)** from left side pane then click on the **+(2)** and select the **Copy Data tool(3)**.

    ![Risk Classification](./images/65.png)

3. Select **Built-in copy task(1)** and click on **Next(2)**.

    ![Risk Classification](./images/66.png)

4. Select for **Source Type : Azure Blob Storage(1)**, **Connection : link_to_sbadata_storage(2)**, **file or folder : testinput(3)** and click on **Next(4)**.

    ![Risk Classification](./images/67.png)

5.  Click on **Preview data(1)** to visualize the data and check the check box for enabling the **first row has the header(2)** and click on  **Next(3)**.

     ![Risk Classification](./images/68.png)
     
6.  Select for **Destination Type : Azure Blob Storage(1)**, **Connection : link_to_sbadata_storage(2)**, **file or folder : testoutput(3)** and click on **Next(4)**.

     ![Risk Classification](./images/69.png)

7. Check the check box for **add header to the file(1)** and click on **Next(2)**.

    ![Risk Classification](./images/70.png)

8. On the setting pane for **Task name : Ingest_test_file(1)** click on **Next(2)**.

    ![Risk Classification](./images/74.png)

9. on the review pane click on **Next**.

    ![Risk Classification](./images/72.png)

10. Once all the validations are succeeded then click on **Finish**.

     ![Risk Classification](./images/73.png)

11. Go to the pipelines and make sure that pipeline run got succeeded.

     ![Risk Classification](./images/75.png)

12. In the Ingest_test_file pipeline click on **New\Edit**.

     ![Risk Classification](./images/76.png)

13. In the Add triggers page click on choose trigger and click on **+New**.

     ![Risk Classification](./images/77.png)

14. Select **Name** : **sbaautojob(1)** , **type** : **Storage events(2)**, **Azure Subscription** : Select the available subscription(3), **Storage account name** : **sbadataDID(4)**, **conatiner name** : **testinput(5)**, check the check box for the **blob created**(6) and click on **continue(7)**.

     ![Risk Classification](./images/78.png)

15. On the datapreview page click on **continue** and click **Ok**.

     ![Risk Classification](./images/79.png)

16. click on publish all and click on **Publish** and wait till publish is completed.

     ![Risk Classification](./images/80.png)

17. Go to **sbadataDID** storage account and select **testinput** container.

     ![Risk Classification](./images/81.png)

18. Click on **upload(1)** and click on **Browse for files(2)**.

     ![Risk Classification](./images/82.png)

19. Select the file in **windows(c:)**, **LabFiles(2)**, Select the **test2.csv(3)** file and click on **open(4)**.

     ![Risk Classification](./images/83.png)

20. click on **upload**.

     ![Risk Classification](./images/84.png)

21. 17. Go to **sbadataDID** storage account and select **testoutput** container.

     ![Risk Classification](./images/85.png)

22. Verify that **test2.csv** file is automatically copied to the **testoutput** container.

     ![Risk Classification](./images/86.png)

