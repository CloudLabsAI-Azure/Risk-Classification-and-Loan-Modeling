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
