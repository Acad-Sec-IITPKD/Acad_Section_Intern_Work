# Problem
The academic section sends a lot of forms, and many times the fields in these forms repeat. We want to make it easier for students by sending forms where repeated fields from old forms are autofilled in any subsequent forms.

# Demo 
Fill this form [Form 1](https://forms.gle/yDqyv96saRoxaBnH9) with `Field 2`(inside form) set to Today's date & check your email.

# Solution 1
## Steps 
1. Let your first form be called Form 1, and its response sheet be called Sheet 1.
2. Open Sheet 1, and for all the fields you want to be prefilled in Form 2, create a new column to format the data. Enter the following formula in the first cell: `=SUBSTITUTE(A2, " ", "+")` (assuming the field you want to be prefilled is in Column A).
   
<img width="370" alt="ss1" src="https://github.com/user-attachments/assets/b1613348-daea-4738-9888-6a1f4af9ef34" />

3. [Optional] If you want the email to be sent on a particular date entered by the form filler in Form 1, create a new column (let's call it "Today" for now) and enter the following formula in the first cell: `=IF(B2=TODAY(), "Yes", "No")` (assuming B2 contains the date on which you want to send the email). **Note that this column auto-updates itself in Google Sheets every day. You can set a time trigger to run the job every 24 hours so that emails will be sent on the date entered in the form.**

<img width="407" alt="Screenshot 2025-01-09 at 8 58 52 PM" src="https://github.com/user-attachments/assets/450f4c7e-c646-4bad-866e-72d1fe9187cf" />

5. Add the Autocrat extension to Sheet 1 & create a job as described in the next steps.

<img width="607" alt="Screenshot 2025-01-09 at 8 59 23 PM" src="https://github.com/user-attachments/assets/94a945ca-cd8e-4906-87cc-ea559d6c2e74" />
<img width="785" alt="Screenshot 2025-01-09 at 9 00 05 PM" src="https://github.com/user-attachments/assets/8174a73f-8d91-46fb-aadf-7d23eaa5ee50" />


6. Add a Google Doc template to Autocrat that you want to be mailed to the form filler.

<img width="750" alt="Screenshot 2025-01-09 at 9 00 37 PM" src="https://github.com/user-attachments/assets/cc3375fa-fbf5-459b-be6a-2785a39e2e47" />

7. You can use the entries filled in the form to automatically update the document being sent by using `<<Column_Name>>` inside the Google Doc. Example:
   ```
   Hi <<Name>>,

   Thank you for filling the form.
   Read this for more information : https://github.com/Acad-Sec-IITPKD/Acad_Section_Intern_Work
   ```
8. Ensure that all Autocrat-generated files are saved in a specific destination folder so it will be easier to clean up the files later.

<img width="730" alt="Screenshot 2025-01-09 at 9 01 06 PM" src="https://github.com/user-attachments/assets/76fc136a-bd78-4aca-810c-79cfac16be3b" />

9. [Optional] Set a merge condition (as shown in the image below) if you want the email to be sent only on a particular date.

<img width="724" alt="Screenshot 2025-01-09 at 9 01 27 PM" src="https://github.com/user-attachments/assets/03cf10ca-c175-496d-91a7-79262e05207d" />

10. Get a prefill link for Form 2.

<img width="444" alt="Screenshot 2025-01-09 at 9 01 48 PM" src="https://github.com/user-attachments/assets/f5756fab-ab1a-4d14-b77c-c60597a172a8" />

11. Include the prefilled link inside the email content, using the formatted columns as parameters inside the link (as shown in the image below).

<img width="723" alt="Screenshot 2025-01-09 at 9 02 39 PM" src="https://github.com/user-attachments/assets/0a94915e-c81c-47c3-88a0-5480f3b01ebb" />

12. Set a time trigger for every 24 hours so that Autocrat runs the job daily.
13. [Optional] If you want two emails to be sent—one immediately after filling out the form with a document and one on a later date entered in the form—you can create two separate Autocrat jobs for the same.
