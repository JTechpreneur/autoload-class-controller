# autoload-class-controller
autoloading class controllers in Code Igniter
/* Creating Core System Classes Admin_Controller and My_Controller in CodeIgniter 3.1.10
here is the spl_autoload_register I used. Make sure your new config.php file 
has configurations same as the other config.php file.To set your own sub-class prefix, open your application/config/config.php        file and look for this item:

$config['subclass_prefix'] = 'MY_';

Please note that all native CodeIgniter libraries are prefixed with CI_ so DO NOT use that as your prefix.
Also Note:  Messing with a core system class has a lot of implications, so make sure you know what you are doing before attempting it.
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
