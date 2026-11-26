# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Design xml files for all operations such as blink, rotate, move, slide, zoom, fade.

Step 6: Display the button operations in MainActivity file.

Step 7: Save and run the application




## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: Guru Prasad D.R.
Registeration Number : 212225040104
*/
```

# activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="220dp"
        android:layout_height="220dp"
        android:adjustViewBounds="true"
        android:contentDescription="Hanuman image"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_chainStyle="packed"
        app:srcCompat="@drawable/hanuman"
        tools:srcCompat="@drawable/hanuman" />

    <!-- Row 1: Blink, Rotate, Fade -->
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:text="Blink"
        app:layout_constraintBottom_toTopOf="@+id/button4"
        app:layout_constraintEnd_toStartOf="@+id/button2"
        app:layout_constraintHorizontal_chainStyle="spread"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView" />

    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Rotate"
        app:layout_constraintBottom_toBottomOf="@+id/button"
        app:layout_constraintEnd_toStartOf="@+id/button3"
        app:layout_constraintStart_toEndOf="@+id/button"
        app:layout_constraintTop_toTopOf="@+id/button" />

    <Button
        android:id="@+id/button3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Fade"
        app:layout_constraintBottom_toBottomOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/button2"
        app:layout_constraintTop_toTopOf="@+id/button" />

    <!-- Row 2: Slide, Move, Zoom -->
    <Button
        android:id="@+id/button4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="Slide"
        app:layout_constraintBottom_toTopOf="@+id/button7"
        app:layout_constraintEnd_toStartOf="@+id/button5"
        app:layout_constraintHorizontal_chainStyle="spread"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button" />

    <Button
        android:id="@+id/button5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Move"
        app:layout_constraintBottom_toBottomOf="@+id/button4"
        app:layout_constraintEnd_toStartOf="@+id/button6"
        app:layout_constraintStart_toEndOf="@+id/button4"
        app:layout_constraintTop_toTopOf="@+id/button4" />

    <Button
        android:id="@+id/button6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Zoom"
        app:layout_constraintBottom_toBottomOf="@+id/button4"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/button5"
        app:layout_constraintTop_toTopOf="@+id/button4" />

    <!-- Row 3: Stop Animation -->
    <Button
        android:id="@+id/button7"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="24dp"
        android:text="Stop Animation"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button4" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

# MainActivity.java
```
package com.example.androidapplication;

import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private ImageView imageView;
    private Button blink, rotate, fade, slide, move, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blink = findViewById(R.id.button);       // Blink
        rotate = findViewById(R.id.button2);     // Rotate
        fade = findViewById(R.id.button3);        // Fade
        slide = findViewById(R.id.button4);       // Slide
        move = findViewById(R.id.button5);        // Move
        zoom = findViewById(R.id.button6);        // Zoom
        stop = findViewById(R.id.button7);        // Stop Animation

        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(slide, R.anim.slide);
        createAnimation(move, R.anim.move);
        createAnimation(zoom, R.anim.zoom);

        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    private void createAnimation(Button button, int animResId) {
        button.setOnClickListener(v -> {
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            imageView.startAnimation(animation);
        });
    }
}
```

# fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />
</set>
```

# move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```

# blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```

# rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```

# slide.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        android:duration="500"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>

```

# zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```

## OUTPUT
<img width="1917" height="1022" alt="Screenshot 2026-11-26 223356" src="https://github.com/user-attachments/assets/b714843f-15db-428c-b52d-0ea64c654170" />
<img width="1917" height="1015" alt="Screenshot 2026-11-26 223431" src="https://github.com/user-attachments/assets/c1852b88-c968-4046-b876-ae2bdfbdcc73" />
<img width="1917" height="1006" alt="Screenshot 2026-11-26 223447" src="https://github.com/user-attachments/assets/a5c1f7e9-8d9a-46bc-89d3-d81f30b59f0d" />
<img width="1917" height="1002" alt="Screenshot 2026-11-26 223512" src="https://github.com/user-attachments/assets/3fdbb4cc-cef7-409b-ad3c-4df6288b34dd" />
<img width="1917" height="1011" alt="Screenshot 2026-11-26 223532" src="https://github.com/user-attachments/assets/88189911-49f9-40da-8b63-973371ca1e72" />
<img width="1917" height="1020" alt="Screenshot 2026-11-26 223559" src="https://github.com/user-attachments/assets/08e931db-3ba7-4924-9816-bb2820750a7c" />
<img width="1917" height="1006" alt="Screenshot 2026-11-26 223617" src="https://github.com/user-attachments/assets/3a049ea3-4ee4-45ff-abd0-7246f9219c1c" />

## RESULT
Thus,the experiment Implementation of Animation application using android studio executed successfully.


## RESULT
