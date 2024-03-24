# Google_form_appscript
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
