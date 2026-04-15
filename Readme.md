# Android Application Development – Practical File
### All 12 Exam Practicals (Complete Write-ups)

---

# PRACTICAL 1
## Aim:
To develop an Android application that displays "Welcome to Mobile Application Development" on the screen.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, Android Virtual Device (AVD)

## Theory:
1. Android is an open-source mobile operating system based on the Linux kernel, developed and maintained by Google.
2. Android Studio is the official Integrated Development Environment (IDE) for Android app development, based on IntelliJ IDEA.
3. Every Android project contains two key files: `activity_main.xml` (defines the UI layout) and `MainActivity.java` (contains the application logic).
4. `TextView` is a fundamental UI widget in Android used to display text on the screen to the user.
5. The `setContentView()` method links the Java activity file with its corresponding XML layout file.
6. The `res/layout/` folder stores all XML layout files that define the visual structure of the application screens.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome to Mobile Application Development"
        android:textSize="22sp"
        android:textStyle="bold"
        android:gravity="center"
        android:padding="16dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical1;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

## Output:
The application displays a screen with the text **"Welcome to Mobile Application Development"** centered on the screen in bold.

## Conclusion:
We successfully created an Android application that displays a welcome message on the screen using the `TextView` widget inside a `LinearLayout`.

---

# PRACTICAL 2
## Aim:
To write an Android program that displays a message when a Button is clicked.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. A `Button` is a UI widget in Android that triggers a specific action when the user taps/clicks it.
2. The `setOnClickListener()` method is used to attach a click event handler to a button widget.
3. `Toast` is a small popup message that appears briefly on the screen to give feedback to the user.
4. `Toast.makeText(context, message, duration).show()` is the complete syntax to display a Toast notification.
5. The `View.OnClickListener` is an interface that must be implemented (or used as a lambda) to handle click events.
6. The `R` class in Android is auto-generated and contains references to all resources defined in the `res/` folder.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <Button
        android:id="@+id/btnClick"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click Me" />

    <TextView
        android:id="@+id/tvMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="18sp"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical2;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnClick = findViewById(R.id.btnClick);
        TextView tvMessage = findViewById(R.id.tvMessage);

        btnClick.setOnClickListener(v -> {
            tvMessage.setText("Hello! Button was Clicked.");
            Toast.makeText(MainActivity.this, "Button Clicked!", Toast.LENGTH_SHORT).show();
        });
    }
}
```

## Output:
When the "Click Me" button is tapped, a Toast popup saying **"Button Clicked!"** appears at the bottom of the screen, and the TextView below the button updates to display **"Hello! Button was Clicked."**

## Conclusion:
We successfully created an Android application that handles button click events and displays feedback to the user using both `Toast` and `TextView`.

---

# PRACTICAL 3
## Aim:
To create an Android application with a layout containing all three button types: Button, ImageButton, and ToggleButton.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `Button` is a standard push button widget that displays text and performs an action when pressed.
2. `ImageButton` is similar to a Button but displays an image/icon instead of text, using the `android:src` attribute.
3. `ToggleButton` is a two-state button that toggles between ON and OFF states using `android:textOn` and `android:textOff` attributes.
4. `setOnClickListener()` is used to handle click events for both `Button` and `ImageButton`.
5. The `isChecked()` method returns the current state (true = ON, false = OFF) of a `ToggleButton`.
6. The `android:src` attribute in `ImageButton` specifies the image resource from the drawable folder.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <Button
        android:id="@+id/btnNormal"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Normal Button"
        android:layout_marginBottom="20dp"/>

    <ImageButton
        android:id="@+id/imgBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@android:drawable/ic_media_play"
        android:layout_marginBottom="20dp"
        android:contentDescription="Image Button"/>

    <ToggleButton
        android:id="@+id/toggleBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textOn="ON"
        android:textOff="OFF"/>

    <TextView
        android:id="@+id/tvResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="16sp"
        android:layout_marginTop="16dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical3;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.ImageButton;
import android.widget.TextView;
import android.widget.Toast;
import android.widget.ToggleButton;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnNormal = findViewById(R.id.btnNormal);
        ImageButton imgBtn = findViewById(R.id.imgBtn);
        ToggleButton toggleBtn = findViewById(R.id.toggleBtn);
        TextView tvResult = findViewById(R.id.tvResult);

        btnNormal.setOnClickListener(v ->
            Toast.makeText(this, "Normal Button Clicked!", Toast.LENGTH_SHORT).show());

        imgBtn.setOnClickListener(v ->
            Toast.makeText(this, "Image Button Clicked!", Toast.LENGTH_SHORT).show());

        toggleBtn.setOnClickListener(v -> {
            if (toggleBtn.isChecked()) {
                tvResult.setText("Toggle is ON");
            } else {
                tvResult.setText("Toggle is OFF");
            }
        });
    }
}
```

## Output:
Three buttons are displayed vertically. Clicking the Normal Button and Image Button shows respective Toast messages. The ToggleButton updates the TextView to show "Toggle is ON" or "Toggle is OFF".

## Conclusion:
We successfully created a layout demonstrating all three button types — `Button`, `ImageButton`, and `ToggleButton` — each with their respective click handlers.

---

# PRACTICAL 4
## Aim:
To write and execute code that counts how many CheckBoxes are checked and displays the count.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `CheckBox` is a type of `CompoundButton` widget in Android that has two states: checked and unchecked.
2. The `isChecked()` method returns `true` if a checkbox is currently checked, `false` otherwise.
3. A counter variable is incremented for every checkbox that returns `true` from `isChecked()`.
4. The `setText()` method dynamically updates the text content of a `TextView` at runtime.
5. The `android:id` attribute assigns a unique identifier to each widget for programmatic access using `findViewById()`.
6. Multiple checkboxes allow the user to select more than one option from a list simultaneously.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Select your hobbies:"
        android:textSize="18sp"
        android:textStyle="bold"
        android:layout_marginBottom="12dp"/>

    <CheckBox android:id="@+id/cb1" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Reading" android:textSize="16sp"/>
    <CheckBox android:id="@+id/cb2" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Gaming" android:textSize="16sp"/>
    <CheckBox android:id="@+id/cb3" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Coding" android:textSize="16sp"/>
    <CheckBox android:id="@+id/cb4" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Travelling" android:textSize="16sp"/>

    <Button
        android:id="@+id/btnCount"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Count Checked"
        android:layout_marginTop="16dp"/>

    <TextView
        android:id="@+id/tvCount"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="18sp"
        android:textStyle="bold"
        android:layout_marginTop="12dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical4;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        CheckBox cb1 = findViewById(R.id.cb1);
        CheckBox cb2 = findViewById(R.id.cb2);
        CheckBox cb3 = findViewById(R.id.cb3);
        CheckBox cb4 = findViewById(R.id.cb4);
        Button btnCount = findViewById(R.id.btnCount);
        TextView tvCount = findViewById(R.id.tvCount);

        btnCount.setOnClickListener(v -> {
            int count = 0;
            if (cb1.isChecked()) count++;
            if (cb2.isChecked()) count++;
            if (cb3.isChecked()) count++;
            if (cb4.isChecked()) count++;
            tvCount.setText("Total Checked: " + count);
        });
    }
}
```

## Output:
Four checkboxes are displayed. The user can check any combination. On clicking **"Count Checked"**, the total number of checked checkboxes is displayed (e.g., "Total Checked: 3").

## Conclusion:
We successfully implemented a checkbox count feature using the `isChecked()` method with a simple counter variable to track and display the total number of selected checkboxes.

---

# PRACTICAL 5
## Aim:
To write and execute code to clear all CheckBoxes and RadioButtons when a Clear button is clicked.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `CheckBox.setChecked(false)` programmatically unchecks a specific checkbox widget.
2. `RadioGroup.clearCheck()` method deselects all `RadioButton` selections within a `RadioGroup` at once.
3. `RadioGroup` is a container ViewGroup that ensures only one `RadioButton` can be selected at a time.
4. `RadioButton` is a two-state button used inside a `RadioGroup` for mutually exclusive options.
5. The `setChecked(boolean)` method can set the checked state of both `CheckBox` and `RadioButton` widgets.
6. A single button click event is used to trigger clearing of all selection states simultaneously across multiple widgets.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView android:layout_width="wrap_content" android:layout_height="wrap_content"
        android:text="CheckBoxes:" android:textStyle="bold" android:textSize="16sp"
        android:layout_marginBottom="4dp"/>

    <CheckBox android:id="@+id/cb1" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Option 1"/>
    <CheckBox android:id="@+id/cb2" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Option 2"/>
    <CheckBox android:id="@+id/cb3" android:layout_width="wrap_content"
        android:layout_height="wrap_content" android:text="Option 3"/>

    <TextView android:layout_width="wrap_content" android:layout_height="wrap_content"
        android:text="Radio Buttons:" android:textStyle="bold" android:textSize="16sp"
        android:layout_marginTop="12dp" android:layout_marginBottom="4dp"/>

    <RadioGroup android:id="@+id/radioGroup" android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <RadioButton android:id="@+id/rb1" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Option A"/>
        <RadioButton android:id="@+id/rb2" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Option B"/>
        <RadioButton android:id="@+id/rb3" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Option C"/>
    </RadioGroup>

    <Button
        android:id="@+id/btnClear"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Clear All"
        android:layout_marginTop="16dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical5;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.RadioGroup;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        CheckBox cb1 = findViewById(R.id.cb1);
        CheckBox cb2 = findViewById(R.id.cb2);
        CheckBox cb3 = findViewById(R.id.cb3);
        RadioGroup radioGroup = findViewById(R.id.radioGroup);
        Button btnClear = findViewById(R.id.btnClear);

        btnClear.setOnClickListener(v -> {
            cb1.setChecked(false);
            cb2.setChecked(false);
            cb3.setChecked(false);
            radioGroup.clearCheck();
            Toast.makeText(this, "All selections cleared!", Toast.LENGTH_SHORT).show();
        });
    }
}
```

## Output:
Three checkboxes and three radio buttons are displayed. After making selections, clicking **"Clear All"** unchecks all checkboxes and deselects all radio buttons, and a Toast message appears.

## Conclusion:
We successfully implemented the functionality to clear all `CheckBox` and `RadioButton` selections simultaneously using `setChecked(false)` and `clearCheck()` methods.

---

# PRACTICAL 6
## Aim:
To write code to change the text color of a RadioButton (and sample text) based on the user's color selection.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `RadioButton` is a UI widget that allows the user to select one option exclusively from a group of options.
2. The `setTextColor()` method changes the text color of any `TextView`-based widget (including RadioButton) at runtime.
3. The `Color` class in Android provides integer color constants like `Color.RED`, `Color.GREEN`, and `Color.BLUE`.
4. `getCheckedRadioButtonId()` returns the resource ID of the currently selected `RadioButton` in a `RadioGroup`.
5. Dynamic property changes in Android are applied programmatically using setter methods during runtime.
6. If no RadioButton is selected, `getCheckedRadioButtonId()` returns `-1`, which can be used to show a warning Toast.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Select a Color:"
        android:textSize="18sp"
        android:textStyle="bold"
        android:layout_marginBottom="12dp"/>

    <RadioGroup
        android:id="@+id/radioGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <RadioButton android:id="@+id/rbRed" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Red" android:textSize="16sp"/>
        <RadioButton android:id="@+id/rbGreen" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Green" android:textSize="16sp"/>
        <RadioButton android:id="@+id/rbBlue" android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:text="Blue" android:textSize="16sp"/>
    </RadioGroup>

    <Button
        android:id="@+id/btnChange"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Change Color"
        android:layout_marginTop="16dp"/>

    <TextView
        android:id="@+id/tvSample"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Sample Text Color"
        android:textSize="22sp"
        android:textStyle="bold"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical6;

import androidx.appcompat.app.AppCompatActivity;
import android.graphics.Color;
import android.os.Bundle;
import android.widget.Button;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        RadioGroup radioGroup = findViewById(R.id.radioGroup);
        RadioButton rbRed = findViewById(R.id.rbRed);
        RadioButton rbGreen = findViewById(R.id.rbGreen);
        RadioButton rbBlue = findViewById(R.id.rbBlue);
        Button btnChange = findViewById(R.id.btnChange);
        TextView tvSample = findViewById(R.id.tvSample);

        btnChange.setOnClickListener(v -> {
            int selectedId = radioGroup.getCheckedRadioButtonId();
            if (selectedId == R.id.rbRed) {
                tvSample.setTextColor(Color.RED);
                rbRed.setTextColor(Color.RED);
            } else if (selectedId == R.id.rbGreen) {
                tvSample.setTextColor(Color.GREEN);
                rbGreen.setTextColor(Color.GREEN);
            } else if (selectedId == R.id.rbBlue) {
                tvSample.setTextColor(Color.BLUE);
                rbBlue.setTextColor(Color.BLUE);
            } else {
                Toast.makeText(this, "Please select a color!", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

## Output:
Three RadioButtons (Red, Green, Blue) are displayed. Selecting a color and clicking **"Change Color"** changes the text color of both the selected RadioButton label and the "Sample Text Color" TextView.

## Conclusion:
We successfully changed the text color of `RadioButton` and `TextView` at runtime using the `setTextColor()` method based on the user's RadioButton selection.

---

# PRACTICAL 7
## Aim:
To implement a circular indeterminate (intermediate) ProgressBar in Android.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `ProgressBar` is a UI widget that visually indicates the progress of an ongoing operation to the user.
2. An **indeterminate** ProgressBar spins continuously without showing a specific percentage, used when task duration is unknown.
3. The style attribute `?android:attr/progressBarStyleLarge` creates a large circular indeterminate ProgressBar.
4. `setVisibility(View.VISIBLE)` makes the ProgressBar appear on the screen dynamically.
5. `setVisibility(View.GONE)` completely hides the ProgressBar and releases its space in the layout.
6. Indeterminate mode is enabled by default for circular ProgressBar; it can also be set using `setIndeterminate(true)` in Java.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <ProgressBar
        android:id="@+id/progressBar"
        style="?android:attr/progressBarStyleLarge"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:visibility="gone"/>

    <TextView
        android:id="@+id/tvStatus"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Press Show to start loading..."
        android:textSize="16sp"
        android:layout_marginTop="16dp"/>

    <Button
        android:id="@+id/btnShow"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Progress"
        android:layout_marginTop="20dp"/>

    <Button
        android:id="@+id/btnHide"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hide Progress"
        android:layout_marginTop="10dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical7;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ProgressBar;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ProgressBar progressBar = findViewById(R.id.progressBar);
        Button btnShow = findViewById(R.id.btnShow);
        Button btnHide = findViewById(R.id.btnHide);
        TextView tvStatus = findViewById(R.id.tvStatus);

        btnShow.setOnClickListener(v -> {
            progressBar.setVisibility(View.VISIBLE);
            tvStatus.setText("Loading... Please wait.");
        });

        btnHide.setOnClickListener(v -> {
            progressBar.setVisibility(View.GONE);
            tvStatus.setText("Loading complete!");
        });
    }
}
```

## Output:
Clicking **"Show Progress"** makes a circular spinning ProgressBar visible on screen with the status text "Loading... Please wait." Clicking **"Hide Progress"** hides the spinner and shows "Loading complete!"

## Conclusion:
We successfully implemented a circular indeterminate ProgressBar in Android to simulate a loading/processing operation using `setVisibility()` with `View.VISIBLE` and `View.GONE`.

---

# PRACTICAL 8
## Aim:
To create a product card UI using FrameLayout in Android.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `FrameLayout` is a ViewGroup that stacks its child views on top of each other in layers, like a stack of cards.
2. It is primarily used to display a single child view, but can be used to overlay multiple views on top of each other.
3. The `android:layout_gravity` attribute controls the positioning of child views within a `FrameLayout`.
4. `FrameLayout` is ideal for creating product cards where text/buttons need to overlay an image.
5. The `android:elevation` attribute adds a drop shadow effect to a view, giving it a card-like appearance.
6. A `LinearLayout` can be nested inside `FrameLayout` using `layout_gravity="bottom"` to overlay content at the bottom of an image.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#F0F0F0">

    <FrameLayout
        android:layout_width="300dp"
        android:layout_height="350dp"
        android:layout_gravity="center"
        android:background="#FFFFFF"
        android:elevation="8dp">

        <ImageView
            android:layout_width="match_parent"
            android:layout_height="220dp"
            android:src="@android:drawable/ic_menu_gallery"
            android:scaleType="centerCrop"
            android:background="#DDDDDD"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="top|end"
            android:background="#FF5722"
            android:text="  NEW  "
            android:textColor="#FFFFFF"
            android:textStyle="bold"
            android:padding="4dp"
            android:layout_margin="8dp"/>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_gravity="bottom"
            android:orientation="vertical"
            android:padding="12dp"
            android:background="#FFFFFF">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Wireless Headphones"
                android:textSize="16sp"
                android:textStyle="bold"/>

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Price: Rs. 1,999"
                android:textColor="#E91E63"
                android:textSize="15sp"
                android:layout_marginTop="4dp"/>

            <Button
                android:id="@+id/btnCart"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="Add to Cart"
                android:layout_marginTop="8dp"/>
        </LinearLayout>
    </FrameLayout>
</FrameLayout>
```

**MainActivity.java**
```java
package com.example.practical8;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnCart = findViewById(R.id.btnCart);
        btnCart.setOnClickListener(v ->
            Toast.makeText(this, "Added to Cart!", Toast.LENGTH_SHORT).show());
    }
}
```

## Output:
A centered product card is displayed showing a placeholder image, a red "NEW" badge in the top-right corner, the product name, price in pink, and an "Add to Cart" button. Clicking the button shows a Toast.

## Conclusion:
We successfully created a product card UI by layering multiple views inside a `FrameLayout`, demonstrating how FrameLayout allows overlapping of child views using `layout_gravity`.

---

# PRACTICAL 9
## Aim:
To design a price summary table using TableLayout in Android.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `TableLayout` is a ViewGroup that displays its children in rows and columns, similar to an HTML `<table>`.
2. Each row in a `TableLayout` is defined using a `TableRow` element containing cells as its children.
3. The `android:stretchColumns` attribute stretches specified columns to fill the remaining available width.
4. Children inside a `TableRow` are treated as cells, placed left to right, each occupying one column.
5. Background colors applied to `TableRow` elements can create alternating row colors for better readability.
6. `TableLayout` does not display borders by default; custom backgrounds are needed to simulate cell borders.

## Program:

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
        android:text="Price Summary"
        android:textSize="22sp"
        android:textStyle="bold"
        android:layout_marginBottom="16dp"/>

    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:stretchColumns="0">

        <TableRow android:background="#3F51B5" android:padding="2dp">
            <TextView android:text="Item" android:textColor="#FFFFFF"
                android:textStyle="bold" android:padding="10dp" android:textSize="15sp"/>
            <TextView android:text="Qty" android:textColor="#FFFFFF"
                android:textStyle="bold" android:padding="10dp" android:textSize="15sp"/>
            <TextView android:text="Price" android:textColor="#FFFFFF"
                android:textStyle="bold" android:padding="10dp" android:textSize="15sp"/>
        </TableRow>

        <TableRow android:background="#FFFFFF">
            <TextView android:text="Laptop" android:padding="10dp"/>
            <TextView android:text="1" android:padding="10dp"/>
            <TextView android:text="Rs.45,000" android:padding="10dp"/>
        </TableRow>

        <TableRow android:background="#F5F5F5">
            <TextView android:text="Mouse" android:padding="10dp"/>
            <TextView android:text="2" android:padding="10dp"/>
            <TextView android:text="Rs.800" android:padding="10dp"/>
        </TableRow>

        <TableRow android:background="#FFFFFF">
            <TextView android:text="Keyboard" android:padding="10dp"/>
            <TextView android:text="1" android:padding="10dp"/>
            <TextView android:text="Rs.1,200" android:padding="10dp"/>
        </TableRow>

        <TableRow android:background="#F5F5F5">
            <TextView android:text="GST (18%)" android:padding="10dp"/>
            <TextView android:text="-" android:padding="10dp"/>
            <TextView android:text="Rs.8,460" android:padding="10dp"/>
        </TableRow>

        <TableRow android:background="#3F51B5">
            <TextView android:text="TOTAL" android:textColor="#FFFFFF"
                android:textStyle="bold" android:padding="10dp" android:textSize="15sp"/>
            <TextView android:text="" android:padding="10dp"/>
            <TextView android:text="Rs.55,460" android:textColor="#FFFFFF"
                android:textStyle="bold" android:padding="10dp" android:textSize="15sp"/>
        </TableRow>
    </TableLayout>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical9;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

## Output:
A well-formatted price summary table is displayed with a blue header row, alternating white/grey item rows, and a blue total row showing the final price.

## Conclusion:
We successfully designed a price summary table using `TableLayout` with styled header and total rows, demonstrating row-based layout management with alternating background colors.

---

# PRACTICAL 10
## Aim:
To design a registration form layout using FrameLayout in Android.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `FrameLayout` as the root layout allows a background color/image to be placed as the bottom layer with the form overlaid on top.
2. `EditText` is a UI widget that provides an input field for users to enter text data in a form.
3. The `android:hint` attribute in `EditText` shows placeholder text (like "Enter Name") when the field is empty.
4. The `android:inputType` attribute defines the keyboard type shown: `textEmailAddress`, `textPassword`, `phone`, etc.
5. `getText().toString()` is used to retrieve the text entered by the user from an `EditText` widget.
6. Form validation is done by checking if fields are empty using `isEmpty()` before processing the submission.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#E8EAF6">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:orientation="vertical"
        android:padding="24dp"
        android:background="#FFFFFF"
        android:layout_margin="24dp"
        android:elevation="6dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Registration Form"
            android:textSize="22sp"
            android:textStyle="bold"
            android:layout_gravity="center"
            android:layout_marginBottom="20dp"/>

        <EditText
            android:id="@+id/etName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Full Name"
            android:inputType="textPersonName"
            android:layout_marginBottom="12dp"/>

        <EditText
            android:id="@+id/etEmail"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Email Address"
            android:inputType="textEmailAddress"
            android:layout_marginBottom="12dp"/>

        <EditText
            android:id="@+id/etPhone"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Phone Number"
            android:inputType="phone"
            android:layout_marginBottom="12dp"/>

        <EditText
            android:id="@+id/etPassword"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Password"
            android:inputType="textPassword"
            android:layout_marginBottom="20dp"/>

        <Button
            android:id="@+id/btnRegister"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Register"/>
    </LinearLayout>
</FrameLayout>
```

**MainActivity.java**
```java
package com.example.practical10;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText etName = findViewById(R.id.etName);
        EditText etEmail = findViewById(R.id.etEmail);
        EditText etPhone = findViewById(R.id.etPhone);
        EditText etPassword = findViewById(R.id.etPassword);
        Button btnRegister = findViewById(R.id.btnRegister);

        btnRegister.setOnClickListener(v -> {
            String name = etName.getText().toString().trim();
            String email = etEmail.getText().toString().trim();
            String phone = etPhone.getText().toString().trim();
            String password = etPassword.getText().toString().trim();

            if (name.isEmpty() || email.isEmpty() || phone.isEmpty() || password.isEmpty()) {
                Toast.makeText(this, "Please fill all fields!", Toast.LENGTH_SHORT).show();
            } else {
                Toast.makeText(this, "Registered Successfully! Welcome " + name, Toast.LENGTH_LONG).show();
            }
        });
    }
}
```

## Output:
A white registration card form is displayed over a blue-tinted background with Name, Email, Phone, and Password fields. Clicking **"Register"** shows either a validation error or a welcome Toast message.

## Conclusion:
We successfully designed a registration form using `FrameLayout` as the root container with a white `LinearLayout` card overlaid on a colored background, including basic form validation.

---

# PRACTICAL 11
## Aim:
To design an Android app that displays a horizontal ProgressBar that progresses from 0% to 100%.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. A horizontal `ProgressBar` in Android shows the progress of a task as a percentage from 0 to 100.
2. The style `?android:attr/progressBarStyleHorizontal` creates a flat horizontal progress bar.
3. The `android:max` attribute defines the maximum value of the ProgressBar (set to 100 for percentage).
4. The `setProgress(int value)` method programmatically updates the current progress value.
5. `Handler` with `post()` is used to update UI components from a background thread safely on the main thread.
6. A background `Thread` is used to simulate incremental progress without blocking the main UI thread.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="24dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Download Progress"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginBottom="20dp"/>

    <ProgressBar
        android:id="@+id/progressBar"
        style="?android:attr/progressBarStyleHorizontal"
        android:layout_width="match_parent"
        android:layout_height="20dp"
        android:max="100"
        android:progress="0"/>

    <TextView
        android:id="@+id/tvPercent"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0%"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginTop="10dp"/>

    <Button
        android:id="@+id/btnStart"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Start Progress"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```

**MainActivity.java**
```java
package com.example.practical11;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.os.Handler;
import android.widget.Button;
import android.widget.ProgressBar;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    int progressStatus = 0;
    Handler handler = new Handler();

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ProgressBar progressBar = findViewById(R.id.progressBar);
        TextView tvPercent = findViewById(R.id.tvPercent);
        Button btnStart = findViewById(R.id.btnStart);

        btnStart.setOnClickListener(v -> {
            progressStatus = 0;
            progressBar.setProgress(0);
            btnStart.setEnabled(false);

            new Thread(() -> {
                while (progressStatus < 100) {
                    progressStatus++;
                    try { Thread.sleep(50); } catch (InterruptedException e) { e.printStackTrace(); }
                    handler.post(() -> {
                        progressBar.setProgress(progressStatus);
                        tvPercent.setText(progressStatus + "%");
                        if (progressStatus >= 100) {
                            btnStart.setEnabled(true);
                            tvPercent.setText("100% - Complete!");
                        }
                    });
                }
            }).start();
        });
    }
}
```

## Output:
Clicking **"Start Progress"** animates the horizontal progress bar from 0% to 100%. The percentage TextView updates in real-time. When complete, it shows **"100% - Complete!"** and the button re-enables.

## Conclusion:
We successfully implemented a horizontal ProgressBar that reaches 100% using a background `Thread` and `Handler` to safely update the UI, demonstrating proper threading in Android.

---

# PRACTICAL 12
## Aim:
To implement a RelativeLayout and add "Add to Cart" and "Buy Now" buttons positioned on opposite ends.

## Requirements:
- **Hardware:** PC/Laptop with minimum 4GB RAM, Android device or emulator
- **Software:** Android Studio, JDK 8+, Android SDK, AVD

## Theory:
1. `RelativeLayout` is a ViewGroup where child views are positioned relative to each other or relative to the parent container.
2. `android:layout_alignParentLeft="true"` positions a view to the left edge of the parent layout.
3. `android:layout_alignParentRight="true"` positions a view to the right edge of the parent layout.
4. `android:layout_alignParentBottom="true"` anchors a view to the bottom of the parent container.
5. `RelativeLayout` eliminates the need for deeply nested layouts, making the UI more flat and efficient.
6. Multiple views can be placed at the same vertical level using `alignParentBottom` with different horizontal anchors.

## Program:

**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <ImageView
        android:id="@+id/imgProduct"
        android:layout_width="match_parent"
        android:layout_height="220dp"
        android:src="@android:drawable/ic_menu_gallery"
        android:background="#CCCCCC"
        android:scaleType="centerCrop"
        android:layout_alignParentTop="true"/>

    <TextView
        android:id="@+id/tvProductName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Premium Smartwatch"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_below="@id/imgProduct"
        android:layout_marginTop="16dp"/>

    <TextView
        android:id="@+id/tvPrice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Price: Rs. 4,999"
        android:textSize="18sp"
        android:textColor="#E91E63"
        android:layout_below="@id/tvProductName"
        android:layout_marginTop="8dp"/>

    <TextView
        android:id="@+id/tvDesc"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="High-quality smartwatch with health tracking, GPS, and 7-day battery life."
        android:textSize="14sp"
        android:layout_below="@id/tvPrice"
        android:layout_marginTop="8dp"/>

    <Button
        android:id="@+id/btnAddToCart"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Add to Cart"
        android:layout_alignParentLeft="true"
        android:layout_alignParentBottom="true"
        android:layout_marginBottom="16dp"/>

    <Button
        android:id="@+id/btnBuyNow"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Buy Now"
        android:layout_alignParentRight="true"
        android:layout_alignParentBottom="true"
        android:layout_marginBottom="16dp"/>
</RelativeLayout>
```

**MainActivity.java**
```java
package com.example.practical12;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btnAddToCart = findViewById(R.id.btnAddToCart);
        Button btnBuyNow = findViewById(R.id.btnBuyNow);

        btnAddToCart.setOnClickListener(v ->
            Toast.makeText(this, "Item added to cart!", Toast.LENGTH_SHORT).show());

        btnBuyNow.setOnClickListener(v ->
            Toast.makeText(this, "Proceeding to checkout...", Toast.LENGTH_SHORT).show());
    }
}
```

## Output:
A product detail page is displayed with an image, product name, price, and description. **"Add to Cart"** appears at the bottom-left and **"Buy Now"** at the bottom-right. Each button shows a Toast message on click.

## Conclusion:
We successfully implemented `RelativeLayout` to position "Add to Cart" and "Buy Now" buttons on opposite ends of the screen using `layout_alignParentLeft` and `layout_alignParentRight` attributes.

---
*End of Practical File — All 12 Practicals Complete*
