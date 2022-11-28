# ImageRotation
Activity 2: Create an App which performs Image Rotation task.
Create the following application using Thread / Service. When the user hits TOGGLE ROTATE button, the
image begin a rotation animation. This button works as a toggle mechanism, which means the image stops
a rotation animation by hitting the button again. The rotation will begin where it leaves off in the previous
animation.

![image](https://user-images.githubusercontent.com/76736494/204349513-5b1514fb-4822-4374-b42f-dffe6ae43a11.png)

Following is the Code of Main Activity in which I have added all the code
package com.example.stopwatch

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.ImageView

class ImageRotation : AppCompatActivity() {
    var flag = false;
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_image_rotation)

        var imageView = findViewById<ImageView>(R.id.imageView)
        Thread{
            while(true){
                if(flag){
                    imageView.rotation = (imageView.rotation+10)%360
                }
                Thread.sleep(100)
            }
        }.start()
    }
    fun handleToggle(view:View){
        flag = !flag
    }
}

Following is the xml code
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ImageRotation">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="144dp"
        android:layout_height="115dp"
        android:layout_marginTop="80dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@android:drawable/btn_star_big_on" />

    <Button
        android:id="@+id/toggleButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="#8E8282"
        android:onClick="handleToggle"
        android:text="TOGGLE BUTTON"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView"
        app:layout_constraintVertical_bias="0.192" />
</androidx.constraintlayout.widget.ConstraintLayout>
