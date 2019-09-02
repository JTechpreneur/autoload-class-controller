# autoload-class-controller
autoloading class controllers in Code Igniter
/* Creating a Admin_Controller and My_Controller in CodeIgniter 3.1.10
   here is the spl_autoload_register I used. Make sure your new config.php file 
   has configurations same as the other config.php file
*/

<?php if ( ! defined('BASEPATH')) exit('No direct script access allowed');

spl_autoload_register(function($class){
	if (stripos($class, 'CI_') !==0) {
		$file = APPPATH . 'libraries/' . $class . '.php';
		if (file_exists($file) && is_file($file)) {
			@include_once($file);			
		}
	}
});		
