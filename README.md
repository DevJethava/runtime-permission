# runtime-permission

[![](https://jitpack.io/v/DevJethava/runtime-permission.svg)](https://jitpack.io/#DevJethava/runtime-permission)

Step 1. Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
Step 2. Add the dependency

	dependencies {
	        implementation 'com.github.DevJethava:runtime-permission:1.0.0'
	}

Sample Code how to used in your project : 


	
public class MainActivity extends MyRuntimePermission {

    String[] permissionRequired;
    int requestCode = 101;

    @RequiresApi(api = Build.VERSION_CODES.O)
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        permissionRequired = new String[]{
                Manifest.permission.WRITE_CALL_LOG,
                Manifest.permission.ACCESS_FINE_LOCATION,
                Manifest.permission.ANSWER_PHONE_CALLS,
                Manifest.permission.RECEIVE_SMS,
                Manifest.permission.SEND_SMS,
                Manifest.permission.WRITE_SYNC_SETTINGS,
                Manifest.permission.WRITE_EXTERNAL_STORAGE
        };

        MainActivity.super.requestAppPermissions(permissionRequired, R.string.permission, requestCode);
    }

    @Override
    public void onPermissionsGranted(int requestCode) {
        if (requestCode == this.requestCode)
            Toast.makeText(this, "Permission Granted Success..", Toast.LENGTH_SHORT).show();
        else {
            Toast.makeText(this, "Permission is Required ..!!", Toast.LENGTH_SHORT).show();
        }
    }
}
