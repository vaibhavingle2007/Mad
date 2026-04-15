# Practical – Bluetooth Paired Devices

## Aim:
To develop an Android application that retrieves and displays a list of paired Bluetooth devices programmatically using the `BluetoothAdapter` class.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device (physical device preferred for Bluetooth), or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. Bluetooth is a short-range wireless communication technology used to exchange data between devices over short distances.
2. `BluetoothAdapter` is the entry point for all Bluetooth interactions in Android; it represents the device's own Bluetooth hardware.
3. `BluetoothAdapter.getDefaultAdapter()` returns the local Bluetooth adapter; if it returns `null`, the device doesn't support Bluetooth.
4. `getBondedDevices()` method of `BluetoothAdapter` returns a `Set<BluetoothDevice>` containing all devices previously paired with the current device.
5. The `BLUETOOTH` permission must be declared in `AndroidManifest.xml`; for Android 12+, `BLUETOOTH_CONNECT` permission is also required.
6. Each `BluetoothDevice` object in the bonded set provides `getName()` and `getAddress()` methods to retrieve the device name and MAC address.

## Program:

**AndroidManifest.xml** *(add inside `<manifest>` tag)*
```xml
<uses-permission android:name="android.permission.BLUETOOTH"/>
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
<uses-permission android:name="android.permission.BLUETOOTH_CONNECT"/>
```

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Paired Bluetooth Devices"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginBottom="12dp"/>

    <Button
        android:id="@+id/btnGetDevices"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Get Paired Devices"/>

    <TextView
        android:id="@+id/tvDevices"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="16sp"
        android:layout_marginTop="16dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.bluetoothpaired;

import androidx.appcompat.app.AppCompatActivity;
import android.bluetooth.BluetoothAdapter;
import android.bluetooth.BluetoothDevice;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;
import java.util.Set;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnGetDevices = findViewById(R.id.btnGetDevices);
        TextView tvDevices = findViewById(R.id.tvDevices);

        btnGetDevices.setOnClickListener(v -> {
            BluetoothAdapter bluetoothAdapter = BluetoothAdapter.getDefaultAdapter();

            if (bluetoothAdapter == null) {
                Toast.makeText(this, "Bluetooth not supported!", Toast.LENGTH_SHORT).show();
                return;
            }

            if (!bluetoothAdapter.isEnabled()) {
                Toast.makeText(this, "Please enable Bluetooth first!", Toast.LENGTH_SHORT).show();
                return;
            }

            Set<BluetoothDevice> pairedDevices = bluetoothAdapter.getBondedDevices();

            if (pairedDevices.size() > 0) {
                StringBuilder sb = new StringBuilder();
                for (BluetoothDevice device : pairedDevices) {
                    sb.append("Name: ").append(device.getName())
                      .append("\nMAC: ").append(device.getAddress())
                      .append("\n\n");
                }
                tvDevices.setText(sb.toString());
            } else {
                tvDevices.setText("No paired devices found.");
            }
        });
    }
}
```

## Output:
On clicking **"Get Paired Devices"**, the app retrieves all previously paired Bluetooth devices and displays each device's **Name** and **MAC Address** in the TextView. If Bluetooth is off, a Toast prompts the user to enable it.

## Conclusion:
We successfully developed an Android application that programmatically retrieves and displays the list of paired Bluetooth devices using `BluetoothAdapter.getBondedDevices()`, demonstrating the use of Android Bluetooth API.
