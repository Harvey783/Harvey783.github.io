---
layout: post
title:      "Send Contact Forms in Heroku Apps to Gmail with PHPMailer"
date:       2019-09-07 08:04:29 +0000
permalink:  send_contact_forms_in_heroku_apps_to_gmail_with_phpmailer
---


Awhile back I ran into a problem with a contact form. I had no idea how to actually make it work. Designing and creating one with HTML/CSS? No problem. Getting the stupid form to send properly to Gmail? Not so much. I never thought sending a form for a Heroku single-page HTML/CSS website could be so difficult. I spent forever trying so many different solutions recommended by tutorials and online resources to no avail. I eventually figured it out but it did take a lot of trial and error. So, to spare someone else the same frustration I went through, here's how to get a contact form.

1. Download, unzip, and add the  [PHPMailer](https://www.dropbox.com/s/079t2fb66j7765v/phpmailer.zip?dl=0) folder to your project's root directory

2.	Go into your Google account. Select 'Security' from the menu on the left and enable 2-Step Verification

3.	While still in 'Security' choose App Passwords. Then choose Select App and choose the app and device you're using. Click 'Generate'. The App Password is the 16-character code in the yellow bar on your device. Copy and paste it somewhere right now

4.	Create a file called sendmail.php in your main project directory, and copy and paste the following.

```
<?php 
    require('phpmailer/PHPMailerAutoload.php');
		
		// NAME, EMAIL, AND MESSAGE ARE VARIABLES FOR YOUR CONTACT FORM FIELDS. THEY CAN BE WHATEVER YOU WANT AND HOWEVER MANY YOU WANT
		
    $name = trim($_POST['name']);
    $email = trim($_POST['email']);
    $message = trim($_POST['message']);
    if($name != null && $email != null && $message != null){
		if(!filter_var($email, FILTER_VALIDATE_EMAIL)) 
		{
		    $signal = 'bad';
            $msg = 'Invalid email. Please check';
        }
        else{
            $mail = new PHPMailer;
            $mail->isSMTP();                                    
            $mail->Host = 'smtp.gmail.com';
            $mail->SMTPAuth = true;                            
            $mail->Username = 'YOUR GMAIL EMAIL ADDRESS';                
            $mail->Password = 'THE APP PASSWORD GENERATED IN THE PREVIOUS STEP';
            $mail->SMTPSecure = 'tsl';                           
            $mail->Port = 587;                                   
            $mail->setFrom('YOUR GMAIL EMAIL ADDRESS';');
            $mail->addAddress('YOUR GMAIL EMAIL ADDRESS';');     
            $mail->addReplyTo($email, $name);
            $mail->isHTML(true);                                  
            $mail->Subject = 'New Contact Form Message';
            $mail->Body    = 'Name: '.$name.' <br />Message: '.$message;
            
            if(!$mail->send()) {
                echo 'Message could not be sent.';
                echo 'Mailer Error: ' . $mail->ErrorInfo;
            } else {
                $signal = 'ok';
                $msg = 'Form submitted';
            }
        }
    }
    else{
        $signal = 'bad';
        $msg = 'Please fill in all the fields.';
    }
    $data = array(
        'signal' => $signal,
        'msg' => $msg
    );
    echo json_encode($data);
?>
```

5. Change your index.html to index.php. Add <?php?> to the top of the file.
6. Create a composer.json file. Add a single pair of curly brackets {} to the file then save. This is needed for whatever reason so Heroku properly deploys your website 


