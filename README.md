# Apex-Email-Utility-with-Merge-Fields

Use Case:   We may have gone through client requirements where they want us to send emails from the Apex code so, in that case we need to configure classic email templates and invoke those templates in apex to send email. Classic Email templates supports fields of the object itself as a merge fields but if we want to insert the parent fields of an object then we need to create Formula fields and use them into the template but if we want to display lot of parent fields we need to create lot of formula fields which is a tedious task.So to get rid of this issue I had created a Utility class which satisfies the above needs.

Technical Details:

We may have the requirement to send email to one single user/contact or public group users so the the utility class will serve both the needs.

EmailNotificationWrapper : A wrapper class to store all the details required for sending an email 
			          This wrapper includes fields :
emailTemplateName - DeveloperName of EmailTemplate
isSendingToTargetObj - Do we need to send email to Target object or not
isSendingToPublicGroup - Do we need to send email to public group users or not
targetObjId - Stores the Id of the target object
userIdList - Stores the List of Users to whom we need to send an email
saveAsActivity - do we need to attach the Email sent to  Activities of target object or not
replaceMergeFieldsMap - Map which stores merge fields with associated values
  
sendCustomNotificationEmail - This method will take parameter as Map of Id and EmailNotificationWrapper and loops over the map and create list of SingleEmailMessage with the data present in the EmailNotificationWrapper , replaces the email body and subject with the replaceMergeFieldsMap values and sends the email

fetchPublicGroupUsers - This method will take parameter as public group name and return the List of Users present in that public group.
