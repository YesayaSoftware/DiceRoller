# DiceRoller
We are going to create a new app project called DiceRoller and add basic interactivity with a button. 
Each time the button is clicked, the value of the displayed text changes. 

* Open the MainActivity layout file and change the “Hello World!” to “Hello Android!”

```xml
    android:text="Hello Android"
```

## Adding the Button
#### 1. Update the layout

```xml
    <?xml version="1.0" encoding="utf-8"?>
    
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        tools:context=".MainActivity">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="30sp"
            android:text="1" />

    </LinearLayout>
```

#### 2. Add another XML tag for the button:

```xml
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:text="@string/roll" />
```

#### 3. Position all views in LinearLayout:	

```xml
    android:layout_gravity="center_vertical"
    android:orientation="vertical"
```

##Connecting the Button

#### 1. Set button’s id in the activity_main.xml layout file
```xml
    android:id="@+id/roll_button"
```

#### 2. Use findViewById to get a reference to the button and assign it to an immutable variable called rollButton:

```kolin
    val rollButton: Button = findViewById(R.id.roll_button)
```

#### 3. (Optional) Dynamically modify the Button view

```kotlin
    rollButton.text = "Let's Roll"
```

##Listen Button when Clicked
#### 1. Make sure that you've completed the steps to findViewById:


#### 2. Set the OnClickListener for the button:

```kotlin
    rollButton.setOnClickListener {

    }
```

#### 3. Make the Toast:

```kotlin
    rollButton.setOnClickListener {
        Toast.makeText(this, "button clicked", Toast.LENGTH_SHORT).show()
    }
```

##Change the Text

#### 1. Assign an id to TextView in the layout
```xml
    android:id="@+id/result_text"
```

#### 2. Remove the Toast and create a method called rollDice:
```kotlin
    rollButton.setOnClickListener {
        rollDice()
    }
```
Generate the method in Android Studio:

#### 3. Write have the rollDice method to get a random number between 1 and 6:

```kotlin
    val randomInt = Random().nextInt(6) + 1
```

#### 4. Use findViewById to get a reference to the TextView and assign it to an immutable variable called resultText:

```kotlin
    val resultText: TextView = findViewById(R.id.result_text)
```

#### 5. Finally, set the random value that you got above as the text of the TextView:
```xml 
    resultText.text = randomInt.toString()
```

##  Adding the Image Resource

[Download the Dice Images](https://github.com/udacity/andfun-kotlin-dice-roller/raw/master/DiceImages.zip)

## Adding the ImageView

#### 1. Add the dice images to the drawable folder

#### 2. Replace TextView with ImageView and assign empty_dice drawable to it:

```xml
    <ImageView
        android:id="@+id/dice_image"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:src="@drawable/empty_dice" />
```

#### 3. Replace reference to the TextView with the ImageView:

```kotlin
    val diceImage: ImageView = findViewById(R.id.dice_image)
```

####C4. Choose the right drawable resource based on the value of randomInt:

```kotlin
    val drawableResource = when (randomInt) {
        1 -> R.drawable.dice_1
        2 -> R.drawable.dice_2
        3 -> R.drawable.dice_3
        4 -> R.drawable.dice_4
        5 -> R.drawable.dice_5
    else -> R.drawable.dice_6
}
```

#### 5. Finally, assign the drawableResource from above to diceImage:

```kotlin
    diceImage.setImageResource(drawableResource)
```

## Finding Views Efficiently

#### 1. Use lateinit to extract the image view variable:

```kotlin
    lateinit var diceImage: ImageView
```

#### 2. Initialize the image view variable:

```kotlin
    diceImage = findViewById(R.id.dice_image)
```

## Namespaces
Previewing images in views

```xml
    xmlns:tools="http://schemas.android.com/tools"
```

```xml
    tools:src="@drawable/dice_1"
```

## Introduction to Gradle
Get to know the structure of the gradle file 

## Android Compatibility

To decide what versions and devices to support

## Vector Drawables

#### 1. Enable the use of support library for vector drawables in build.gradle file (app level):

```kotlin
    vectorDrawables.useSupportLibrary = true
```

#### 2. Use app:srcCompat in the image tag in the layout file:

```xml
    app:srcCompat="@drawable/empty_dice"
```

#### 3. You’ll also need to add the namespace to the root of the layout:

```xml
    xmlns:app="http://schemas.android.com/apk/res-auto"
```



