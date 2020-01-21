$(function() {
  
  var form = $("#form");
  enableFastFeedback(form); 

  form.submit(function(event){
   var name = $("#name").val();
   var password = $("#password").val();
   var message = $("#message").val();
   var checked = $("#checkbox").is(":checked");

   validateNameField(name, event);
   validatePasswordField(password, event);
   validateMessageField(message, event);
   validateCheckboxField(checked, event);
  });
  
});

function enableFastFeedback(formElement){
 var nameInput = formElement.find("#name");
   var passwordInput = formElement.find("#password");
   var messageInput = formElement.find("#message");
   var checkboxInput = formElement.find("#checkbox");

   nameInput.blur(function(event){
   	var name = $(this).val();
   	validateNameField(name, event);

   	if(!isValidName(name)){
   		$(this).css({"box-shadow" : "0 0 4px #811", "border" : "1px solid #600"});
   	}else {
   		$(this).css({"box-shadow" : "0 0 4px #181", "border" : "1px solid #060"});
   	}
   });
  
  passwordInput.blur(function(event){
   	var password = $(this).val();
   	validatePasswordField(password, event);

   	if(!isValidPassword(password)){
   		$(this).css({"box-shadow" : "0 0 4px #811", "border" : "1px solid #600"});
   	}else {
   		$(this).css({"box-shadow" : "0 0 4px #181", "border" : "1px solid #060"});
   	}
   });

  messageInput.blur(function(event){
   	var message = $(this).val();
   	validateMessageField(message, event);

   	if(!isValidMessage(message)){
   		$(this).css({"box-shadow" : "0 0 4px #811", "border" : "1px solid #600"});
   	}else {
   		$(this).css({"box-shadow" : "0 0 4px #181", "border" : "1px solid #060"});
   	}
   });

  checkboxInput.change(function(event){
   	var isChecked = $(this).is(":checked");
   	validateCheckboxField(isChecked, event);

   	if(!isChecked){
   		$(this).css({"box-shadow" : "0 0 4px #811", "border" : "1px solid #600"});
   	}else {
   		$(this).css({"box-shadow" : "0 0 4px #181", "border" : "1px solid #060"});
   	}
   });

}

function validateNameField(name, event) {
	if(!isValidName(name)){
		$("#name-feedback").text("Please enter at least two charecters");
		event.preventDefault();
	}else{
		$("#name-feedback").text("");
	}
}

function isValidName(name){
	return name.length >=2;
}


function validatePasswordField(password, event) {
	if(!isValidPassword(password)){
		$("#password-feedback").text("Please enter at least six charecters and contain a number");
		event.preventDefault();
	}else{
		$("#password-feedback").text("");
	}
}

function isValidPassword(password){
	return password.length >=6 && /.*[0-9].*/.test(password);
}


function validateMessageField(message, event) {
	if(!isValidMessage(message)){
		$("#message-feedback").text("Please enter a valid messgae");
		event.preventDefault();
	}else{
		$("#message-feedback").text("");
	}
}

function isValidMessage(message){
	return message.trim() != "";
}


function validateCheckboxField(isChecked, event) {
	if(!isChecked){
		$("#checkbox-feedback").text("Please agree to this.");
		event.preventDefault();
	}else{
		$("#checkbox-feedback").text("");
	}
}
