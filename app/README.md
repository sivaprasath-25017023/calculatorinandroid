## Ex_5_-Develop a simple calculator using android studio.
Develop a program to create a simple calculator using Android Studio.

## AIM:
To develop a program to create a simple calculator using Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Min. required Artic Fox)

## ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as SMSIntent and click Next.

Step 3: Select the Minimum SDK below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally, click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Perform the Calculator Operation in MainActivity.java

Step 7: Save and run the application.

## Program:
```
/*
Program to create simple calculator using Android Studio.
Developed by: Sivaprasath R
RegisterNumber: 212224243007
*/
```

## MainActivity.java:
```
package com.example.simplecalculator;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private TextView resultText;
    private String currentInput = "";
    private double firstNumber = 0.0;
    private String operator = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        resultText = findViewById(R.id.resultText);

        setNumericButtonClickListener();
        setOperatorButtonClickListener();

        findViewById(R.id.buttonClear).setOnClickListener(v -> {
            currentInput = "";
            firstNumber = 0.0;
            operator = "";
            resultText.setText("0");
        });
    }

    private void setNumericButtonClickListener() {
        View.OnClickListener listener = v -> {
            Button button = (Button) v;
            currentInput += button.getText().toString();
            resultText.setText(currentInput);
        };

        findViewById(R.id.button0).setOnClickListener(listener);
        findViewById(R.id.button1).setOnClickListener(listener);
        findViewById(R.id.button2).setOnClickListener(listener);
        findViewById(R.id.button3).setOnClickListener(listener);
        findViewById(R.id.button4).setOnClickListener(listener);
        findViewById(R.id.button5).setOnClickListener(listener);
        findViewById(R.id.button6).setOnClickListener(listener);
        findViewById(R.id.button7).setOnClickListener(listener);
        findViewById(R.id.button8).setOnClickListener(listener);
        findViewById(R.id.button9).setOnClickListener(listener);
        findViewById(R.id.buttonDot).setOnClickListener(listener);
    }

    private void setOperatorButtonClickListener() {
        View.OnClickListener operatorListener = v -> {
            Button button = (Button) v;
            if (!currentInput.isEmpty()) {
                firstNumber = Double.parseDouble(currentInput);
                operator = button.getText().toString();
                currentInput = "";
            }
        };

        findViewById(R.id.buttonAdd).setOnClickListener(operatorListener);
        findViewById(R.id.buttonSubtract).setOnClickListener(operatorListener);
        findViewById(R.id.buttonMultiply).setOnClickListener(operatorListener);
        findViewById(R.id.buttonDivide).setOnClickListener(operatorListener);
        findViewById(R.id.buttonEqual).setOnClickListener(v -> {
            if (!currentInput.isEmpty()) {
                double secondNumber = Double.parseDouble(currentInput);
                double result;

                switch (operator) {
                    case "+":
                        result = firstNumber + secondNumber;
                        break;
                    case "-":
                        result = firstNumber - secondNumber;
                        break;
                    case "*":
                        result = firstNumber * secondNumber;
                        break;
                    case "/":
                        result = secondNumber != 0 ? firstNumber / secondNumber : 0; // Avoid division by zero
                        break;
                    default:
                        return;
                }
                resultText.setText(String.valueOf(result));
                currentInput = "";
            }
        });
    }
}

```

## activity_main.xml:
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:background="#717171"
    android:padding="16dp">

    <TextView
        android:id="@+id/resultText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="32sp"
        android:gravity="end"
        android:padding="18dp"
        android:background="@drawable/rounded_corner"/>

    <GridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:rowCount="5"
        android:columnCount="4"
        android:padding="8dp"
        android:background="#262626"
        android:layout_marginTop="16dp"
        android:layout_marginBottom="16dp">

        <!-- Row 1 -->
        <Button android:text="7" android:id="@+id/button7" style="@style/CalculatorButton"/>
        <Button android:text="8" android:id="@+id/button8" style="@style/CalculatorButton"/>
        <Button android:text="9" android:id="@+id/button9" style="@style/CalculatorButton"/>
        <Button android:text="/" android:id="@+id/buttonDivide" style="@style/CalculatorButton"/>

        <!-- Row 2 -->
        <Button android:text="4" android:id="@+id/button4" style="@style/CalculatorButton"/>
        <Button android:text="5" android:id="@+id/button5" style="@style/CalculatorButton"/>
        <Button android:text="6" android:id="@+id/button6" style="@style/CalculatorButton"/>
        <Button android:text="*" android:id="@+id/buttonMultiply" style="@style/CalculatorButton"/>

        <!-- Row 3 -->
        <Button android:text="1" android:id="@+id/button1" style="@style/CalculatorButton"/>
        <Button android:text="2" android:id="@+id/button2" style="@style/CalculatorButton"/>
        <Button android:text="3" android:id="@+id/button3" style="@style/CalculatorButton"/>
        <Button android:text="-" android:id="@+id/buttonSubtract" style="@style/CalculatorButton"/>

        <!-- Row 4 -->
        <Button android:text="0" android:id="@+id/button0" style="@style/CalculatorButton"/>
        <Button android:text="." android:id="@+id/buttonDot" style="@style/CalculatorButton"/>
        <Button android:text="=" android:id="@+id/buttonEqual" style="@style/CalculatorButton"/>
        <Button android:text="+" android:id="@+id/buttonAdd" style="@style/CalculatorButton"/>

        <!-- Clear Button -->
        <Button
            android:id="@+id/buttonClear"
            style="@style/ClearButton"
            android:layout_columnSpan="4"
            android:text="C"/>

    </GridLayout>

</LinearLayout>


```

## Output:
<img width="1919" height="1141" alt="image" src="https://github.com/user-attachments/assets/da075ea1-fadf-4f57-95e6-a746bd61028b" />

<img width="421" height="985" alt="image" src="https://github.com/user-attachments/assets/58a90e85-24b0-4de0-b755-cd975cbd9a4b" />



## Result:
Thus a Simple Android Application to create a calculator using Android Studio was developed and executed successfully.
