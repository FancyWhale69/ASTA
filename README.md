# Google_form_appscript

## Goal
This repo aims to provide a quick refrence to build appscripts for specific tasks to allow quick automation of said tasks.

# Tasks List
 - [Fill google forms using google sheets](Fill-google-forms-using-google-sheets)
     - [Skelton Code](Skelton-Code) 
 - [Notes](Notes)

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
     form.addMultipleChoiceItem()
    .setTitle(row[1]+'Do you prefer cats or dogs?')
    .setChoiceValues(['Cats','Dogs'])
    .showOtherOption(true);

         form.addMultipleChoiceItem()
    .setTitle(row[0]+'Do you prefer cats?')
    .setChoiceValues(['yes','no'])
    .showOtherOption(true);

 }
 // Log the URLs for the form
 Logger.log('Published URL: ' + form.getPublishedUrl());
 Logger.log('Editor URL: ' + form.getEditUrl());
}
```

## Notes
