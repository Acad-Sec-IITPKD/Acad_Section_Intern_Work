# Problem
The academic section sends a lot of forms, and many times the fields in these forms repeat. We want to make it easier for students by sending forms where repeated fields from old forms are autofilled in any subsequent forms.

# Demo 
Fill this form [Form 1](https://forms.gle/yDqyv96saRoxaBnH9) with `Field 2`(inside form) set to Today's date & check your email.

# Solution 1
## Steps 
1. Let your first form be called Form 1, and its response sheet be called Sheet 1.
2. Open Sheet 1, and for all the fields you want to be prefilled in Form 2, create a new column to format the data. Enter the following formula in the first cell: `=SUBSTITUTE(A2, " ", "+")` (assuming the field you want to be prefilled is in Column A).
<img width="370" alt="ss1" src="https://github.com/user-attachments/assets/b1613348-daea-4738-9888-6a1f4af9ef34" /> 
4. [Optional] If you want the email to be sent on a particular date entered by the form filler in Form 1, create a new column (let's call it "Today" for now) and enter the following formula in the first cell: `=IF(B2=TODAY(), "Yes", "No")` (assuming B2 contains the date on which you want to send the email). **Note that this column auto-updates itself in Google Sheets every day. You can set a time trigger to run the job every 24 hours so that emails will be sent on the date entered in the form.**
  <<Image 2>>
5. Add the Autocrat extension to Sheet 1 & create a job as described in next steps.
<<Image 3 & 4>>
6. Add a Google Doc template to Autocrat that you want to be mailed to the form filler.
<<Image 5>>
7. You can use the entries filled in the form to automatically update the document being sent by using `<<Column_Name>>` inside the Google Doc. Example:
   ```
   Hi <<Name>>,

   Thank you for filling the form.
   Read this for more information : https://github.com/Acad-Sec-IITPKD/Acad_Section_Intern_Work
   ```
8. Ensure that all Autocrat-generated files are saved in a specific destination folder so it will be easier to clean up the files later.
<<Image 6>>
9. [Optional] Set a merge condition (as shown in the image below) if you want the email to be sent only on a particular date.
<<Image 7>>
10. Get a prefill link for Form 2.
<<Image 8>> 
11. Include the prefilled link inside the email content, using the formatted columns as parameters inside the link (as shown in the image below).
<<Image 9>>
12. Set a time trigger for every 24 hours so that Autocrat runs the job daily.
13. [Optional] If you want two emails to be sent—one immediately after filling out the form with a document and one on a later date entered in the form—you can create two separate Autocrat jobs for the same.
