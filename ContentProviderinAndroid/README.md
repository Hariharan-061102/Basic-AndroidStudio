# Ex.No:3 Create Your Own Content Providers
## AIM:
To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Min. required Artic Fox)

## ALGORITHM:
### Step 1: 
Open Android Stdio and then click on File -> New -> New project.

### Step 2:
Then type the Application name as “ex.no.3″ and click Next.

### Step 3: 
Then select the Minimum SDK as shown below and click Next.

### Step 4: 
Then select the Empty Activity and click Next. Finally click Finish.

### Step 5: 
Design layout in activity_main.xml.

### Step 6: 
Get contacts details and Display details give in MainActivity file.

### Step 7: 
Save and run the application.

## PROGRAM
```
/*
Program to print the text create your own content providers to get contacts details.
Developed by: Hariharan M
Registeration Number : 212221230034
*/
```
## MainActivity.java
```
package com.example.contentprov;

import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.provider.MediaStore;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {

    private final int GALLERY_REQ_CODE = 1000;
    ImageView imgGallery;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imgGallery = findViewById(R.id.imgGallery);
        Button btnGallery = findViewById(R.id.btnGallery);

        btnGallery.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent iGallery = new Intent(Intent.ACTION_PICK);
                iGallery.setData(MediaStore.Images.Media.EXTERNAL_CONTENT_URI);
                startActivityForResult(iGallery, GALLERY_REQ_CODE);
            }
        });

    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if(resultCode==RESULT_OK){
            if(requestCode==GALLERY_REQ_CODE){
                imgGallery.setImageURI(data.getData());
            }
        }
    }
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imgGallery"
        android:layout_width="286dp"
        android:layout_height="295dp"
        android:layout_marginTop="60dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btnGallery"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Open Gallery"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imgGallery" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT
![](1.png)
![](2.png)
## RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.