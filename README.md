# Develop an Android Application Using TableLayout to Design a Structured Login/Registration Form

[← Back to Index](README.md)

**Project Name:** TableLayout

## Aim

To develop an Android application using `TableLayout` to design a structured Student Registration Form.

## I. Filename: `activity_main.xml`

**Location:** `app/src/main/res/layout/activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    android:id="@+id/main"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="16dp"
        android:stretchColumns="1"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <!-- Heading -->
        <TableRow>
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_span="2"
                android:gravity="center"
                android:text="Student Registration"
                android:textSize="28sp"
                android:textStyle="bold"
                android:padding="16dp" />
        </TableRow>

        <!-- Name -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Name"
                android:textSize="18sp"
                android:padding="8dp" />

            <EditText
                android:id="@+id/etName"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Name"
                android:inputType="textPersonName" />
        </TableRow>

        <!-- Email -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Email"
                android:textSize="18sp"
                android:padding="8dp" />

            <EditText
                android:id="@+id/etEmail"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Email"
                android:inputType="textEmailAddress" />
        </TableRow>

        <!-- Password -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Password"
                android:textSize="18sp"
                android:padding="8dp" />

            <EditText
                android:id="@+id/etPassword"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Password"
                android:inputType="textPassword" />
        </TableRow>

        <!-- Buttons -->
        <TableRow
            android:gravity="center"
            android:paddingTop="20dp">

            <Button
                android:id="@+id/btnRegister"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Register" />

            <Button
                android:id="@+id/btnReset"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="20dp"
                android:text="Reset" />

        </TableRow>

    </TableLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```

## II. Filename: `MainActivity.java`

**Location:** `app/src/main/java/com/example/tabledemo/MainActivity.java`

```java
package com.example.tabledemo;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText etName, etEmail, etPassword;
    private Button btnRegister, btnReset;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etName = findViewById(R.id.etName);
        etEmail = findViewById(R.id.etEmail);
        etPassword = findViewById(R.id.etPassword);

        btnRegister = findViewById(R.id.btnRegister);
        btnReset = findViewById(R.id.btnReset);

        btnRegister.setOnClickListener(v -> {
            String name = etName.getText().toString().trim();
            String email = etEmail.getText().toString().trim();
            String password = etPassword.getText().toString();

            if (name.isEmpty() || email.isEmpty() || password.isEmpty()) {
                Toast.makeText(
                    this,
                    "Please fill in all fields",
                    Toast.LENGTH_SHORT
                ).show();
            } else {
                Toast.makeText(
                    this,
                    "Registration submitted",
                    Toast.LENGTH_SHORT
                ).show();
            }
        });

        btnReset.setOnClickListener(v -> {
            etName.setText("");
            etEmail.setText("");
            etPassword.setText("");
        });
    }
}
```

## Explanation

1. **ConstraintLayout:** Acts as the parent layout and positions the `TableLayout` at the top of the screen.
2. **TableLayout:** Organizes the form components into rows and columns.
3. **TableRow:** Places labels and input fields in individual rows.
4. **TextView:** Displays the heading and field labels such as Name, Email, and Password.
5. **EditText:** Allows the user to enter registration details.
6. **Register Button:** Checks whether all fields are filled and displays a confirmation message.
7. **Reset Button:** Clears all input fields.
8. **Input Types:** The email field accepts email-style input, while the password field masks the entered characters.

## Output

The application displays a Student Registration Form containing:

- Name input field
- Email input field
- Password input field
- Register button
- Reset button

When the user clicks **Register** with empty fields, the application displays "Please fill in all fields". When all fields are filled, it displays "Registration submitted". Clicking **Reset** clears all fields.

## Result

Thus, an Android application using `TableLayout` to design a structured Student Registration Form was developed successfully.
