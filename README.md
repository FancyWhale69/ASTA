# Appscript Skeleton for Task Automation

## Goal
This repo aims to provide a quick refrence to build appscripts for specific tasks to allow quick automation of said tasks.

# Tasks List
 - [Fill google forms using google sheets](#fill-google-forms-using-google-sheets)
     - [Skelton Code](#skelton-code)
 - [How to make an appscript](#how-to-make-an-appscript)
 - [Notes](#notes)

# Fill google forms using google sheets
This Task consist of creating a Google Form from elements present in a seperate Google Sheet. For example making a form where users answers question related to a text, where said text is pulled
from a seperate Google Sheet.

## Skelton Code
```
function main() {
 // Replace 'SPREADSHEET_ID' with your actual spreadsheet ID
 var spreadsheetId = 'SPREADSHEET_ID';
 var sheet = SpreadsheetApp.openById(spreadsheetId).getActiveSheet();
 var form = FormApp.create('FORM_NAME');
form.setDescription('FORM_DESCRIPTION')

 var data = sheet.getDataRange().getValues();
 for (var i = 1; i < data.length; i++) {
    var row = data[i];
    //ADD QUESTION ELEMNTS FOR EXAMPLE
     //form.addMultipleChoiceItem()
    //.setTitle(row[1]+'Do you prefer cats or dogs?')
    //.setChoiceValues(['Cats','Dogs'])
    //.showOtherOption(true);

        // form.addMultipleChoiceItem()
   // .setTitle(row[0]+'Do you prefer cats?')
   // .setChoiceValues(['yes','no'])
   // .showOtherOption(true);

 }
 // Log the URLs for the form
 Logger.log('Published URL: ' + form.getPublishedUrl());
 Logger.log('Editor URL: ' + form.getEditUrl());
}
```
### explaination
`SPREADSHEET_ID`: The ID of the google sheet which you want to pull info from, which can be found here `https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit#gid=0`.  
`FORM_NAME`: The name you wish to give your form, for example "MOS for Text Generation".  
`FORM_DESCRIPTION`: The description which may be used to explain the expected task from the users.  
`var form`: The variable which is used to add questions/elements to the created form.  
`var row`: A row which contains all the values in that row, ordered the same way in the sheet, for example the sheet is ordered as ('file_name', 'question_1', 'question_2') then row will contain the values in the same order ('1223.txt', 'do you like cats?', 'do you eat meat?').  
`var data`: Contains all the values in the sheet. (Almost like a DataFrame).  

For the complete list of all questions types and elements for Form class please visit the following [page](https://developers.google.com/apps-script/reference/forms/form)   

## How to make an appscript
1. Visit the [AppScript](https://www.google.com/script/start/) page.
2. Start a new project.
3. Copy the code skeleton for the desired task.
4. Fill in the values for the specified variables.
5. Add the desired elements.
6. ???
7. Save & run the app. 

## Notes
If you want a task to be added please open an issue or contact me.  
Or make a pull request if you have a code for specific task that is not present.
