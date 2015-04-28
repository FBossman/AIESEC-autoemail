# AIESEC-autoemail
# Autoemail from gmail
# contact Fahim Rahman (fahim2.rahman@aiesec.net) for info, help, questions, or whatever you want :)

 var ss = SpreadsheetApp.getActiveSpreadsheet();
 var sheet = ss.getSheets()[0];

 // This logs the value in the very last cell of this sheet
 var lastRow = sheet.getLastRow();
 var lastColumn = sheet.getLastColumn();
 var lastCell = sheet.getRange(lastRow, lastColumn);
 Logger.log(lastCell.getValue());

var EMAIL_SENT = "EMAIL_SENT";

function sendEmails2() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var startRow = 2;  // First row of data to process
  var numRows = lastRow;   // Number of rows to process = the last row
  // Fetch the range of cells
  var dataRange = sheet.getRange(startRow, 1, numRows, 5)
  sheet.getrange
  // Fetch values for each row in the Range.
  var data = dataRange.getValues();
  for (var i = 0; i < data.length; ++i) {
    var row = data[i];
    var emailAddress = row[3];  // 4rd column
    var firstname = row[1];
    var message = ("Welcome " + firstname + ", \r \r how are you?\r www.google.com\r www.expa.com")
    var emailSent = row[4];     // 5rd column
    if (emailSent != EMAIL_SENT) {  // Dont send email if I already emailed them
      var subject = "Sending emails from a Spreadsheet";
      MailApp.sendEmail(emailAddress, subject, message);
      sheet.getRange(startRow + i, 5).setValue(EMAIL_SENT);
      // Update cells immediately
      SpreadsheetApp.flush();
    }
  }
}
