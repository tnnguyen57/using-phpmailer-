# using-phpmailer-
I am trying to install phpmailer to use php to send email from localhost xampp
I am trying to install phpmailer without running a composer because my window 10 laptop does not have a composer and it is too complicated
to install a composer, but I can not get the script to work because I am a beginning programmer.
I installed phpmailer by the way of download zip.
below is my code:

<?php
    
use PHPMailer\PHPMailer\PHPMailer;
//use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

require 'PHPMailer-master/src/Exception.php';
require 'PHPMailer-master/src/PHPMailer.php';
require 'PHPMailer-master/src/SMTP.php';

$mail = new PHPMailer;

$mail->isSMTP();                           // Set mailer to use SMTP		
$mail->SMTPAuth = true;               // Enable SMTP authentication
$mail->SMTPDebug = 3;
$mail->Host = 'smtp.gmail.com';    // Specify main and backup SMTP servers

//$mail->SMTPAuth = true;               // Enable SMTP authentication
	//$mail->SMTPDebug = 2;
$mail->Username = 'thomas.nhat.nguyen@gmail.com';    // SMTP username
$mail->Password = 'Suc-57-cess'; // SMTP password
$mail->SMTPSecure = 'tls';      // Enable TLS encryption, `ssl` also accepted
//$mail->Port = 465;                  // TCP port to connect to
$mail->Port = 587;
//$mail->Port = 25;
	

$mail->setFrom('thomas.nhat.nguyen@gmail.com', 'Thomas Nguyen');
$mail->addReplyTo('thomas.nhat.nguyen@gmail.com', 'Thomas Nguyen');
//$mail->addAddress('lethinguyen1933@gmail.com');   // Add a recipient
//$mail->addCC('cc@gmail.com');             //Add cc Address
//$mail->addBCC('bcc@gmail.com');         //Add bcc Address

$mail->isHTML(true);  // Set email format to HTML
$mail->Subject = $_POST['subject'];
$mail->Body     = $_POST['message'];
	$mail->AltBody = 'HTML messaging not supported';
$mail->addAddress($_POST['mailto']);   // Add a recipient
		
/*$mail->smtpConnect(
	array(
		"ssl" => array(
				"verify_peer" => false,
				"verify_peer_name" => false,
				"allow_self_signed" => true
		)
	)
);*/
		
/*$mail->SMTPOptions = array(
	'ssl' => array(
			'verify_peer' => false,
			'verify_peer_name' => false,
			'allow_self_signed' => true
	)
);*/
		
var_dump($mail->send());

/*if(!$mail->send())
{
echo 'Message could not be sent.';
echo 'Mailer Error: ' . $mail->ErrorInfo;
}
else
{
echo 'Message has been sent';
}*/

?>
