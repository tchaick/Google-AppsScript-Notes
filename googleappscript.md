### Google App Script - Seminar Workshop 
March 15 - 16, 2023



### Creating a Google Doc

Create a new Google Document with the name "Juanito Doc" and append a new paragraph containing the text "Hello World" to its body.

```
function myFunction1() {
  var doc = DocumentApp.create('Juanito Doc'); //creates the doc named Juanito Doc
  var body = doc.getBody(); //pulls the body of the doc assigned to variable body
  body.appendParagraph('Hello World'); //adds a new paragraph to the body with the text Hello World. 
}
```



### Creating a Google Doc containing a header and paragraphs

Create a new Google Docs document using the DocumentApp.create() method, sets the document title to "Juanito Doc - Hello World", insert a new paragraph at the beginning of the document with the text "Hello World" and set its heading style to HEADING1, and then insert three additional paragraphs with the text "First Paragraph", "Second Paragraph", and "Third Paragraph" at the respective positions of 2, 3, and 4 within the document's body.


```
function myFunction2(){
 var doc = DocumentApp.create('Juanito Doc - Hello World');
 var body = doc.getBody();
 var heading = body.insertParagraph(0,'Hello World');
  heading.setHeading(DocumentApp.ParagraphHeading.HEADING1);
  body.insertParagraph(2, 'First Paragraph');
  body.insertParagraph(3, 'Second Paragraph');
  body.insertParagraph(4, 'Third Paragraph');
}
```



### Send Google Doc to a recipient email

Create a new Google Document with the name "Juanito Doc Email", append a new paragraph with the text "Hello World" to its body, retrieve the email address of the active user, set the subject of the email to the name of the document, and compose an email containing the URL of the newly created document. The email is then sent to the email address of the active user.


```
function myFunction3() {

  var doc = DocumentApp.create('Juanito Doc Email'); // creates a new Google Document with the title "Juanito Doc Email" and assigns it to the variable doc.

  var body = doc.getBody(); //assigns the body of the newly created document to the variable body

  body.appendParagraph('Hello World'); // adds a new paragraph to the body of the document with the text "Hello World".
  
  var email = Session.getActiveUser().getEmail(); //retrieves the email address of the active user and assigns it to the variable email.

  var subject = doc.getName(); // retrieves the name of the document and assigns it to the variable subject.

  var bodyEmail = 'This is the new doc = ' + doc.getUrl(); // composes the body of the email by concatenating the string "This is the new doc =" with the URL of the newly created document, which is obtained using the getUrl() method of the Document class.

  GmailApp.sendEmail(email, subject,bodyEmail); // sends an email to the email address of the active user, with the subject set to the name of the document and the body set to the bodyEmail variable. The sendEmail() method is a function of the GmailApp class.
}
```

