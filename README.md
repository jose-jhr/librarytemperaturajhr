# librarytemperaturajhr
Libreria custom view termometro, puede ser usado para animar las diferentes tareas o recibir datos de diferentes microcontroladores.


![termometro](https://user-images.githubusercontent.com/66834393/173481984-32a6618f-ed14-4f5d-b9e8-1dcfc92d07a8.png)

para descargar esta libreria 

```
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  ```
  
```
 dependencies {
	        implementation 'com.github.jose-jhr:librarytemperaturajhr:0.1.0'
	}
  ```
  en la nueva version de android se realiza las siguiente tareas.
  
  ```
  dependencies {
	        implementation 'com.github.jose-jhr:librarytemperaturajhr:Tag'
	}
  ```

  
  
![settingsgradle](https://user-images.githubusercontent.com/66834393/173482298-037dbbed-f8d1-4421-bdf0-9e38a53854fc.png)
  
![image](https://user-images.githubusercontent.com/66834393/173484979-059ab354-0653-40de-8d8d-99e3c76591bb.png)

  
![dependencies](https://user-images.githubusercontent.com/66834393/173483467-0baec9b0-81d4-451b-9b11-ce46308ad48a.png)


![maven](https://user-images.githubusercontent.com/66834393/173482552-49f0c974-c4d7-4502-b308-37609e9afe36.png)









CODIGO DE EJEMPLO PARA LA UTILIZACIÓN DE ESTA LIBRERIA.

activity_main.xml

 ```
 <?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:orientation="vertical"
    >

    <com.ingenieriajhr.termometrojhr.TermometroJhr
        android:id="@+id/termometro"
        android:layout_width="335dp"
        android:layout_height="472dp"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true"
        app:colorTemperatura="#EB0008"
        app:colorTermometro="#000003"
        app:offsetX="-35"
        app:offsetY="-10"
        app:textColorTemp="#3D5AFE"
        app:textSizeTemp="30"
        android:layout_gravity="center"
        app:textTemp=" K"
        app:textOn="true"
        >
    </com.ingenieriajhr.termometrojhr.TermometroJhr>



    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        >

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/mas"
            android:layout_marginTop="10dp"
            android:text="mas"
            ></Button>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/menos"
            android:layout_alignParentEnd="true"
            android:layout_marginTop="10dp"
            android:text="menos"
            ></Button>

        <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@id/mas"
            android:layout_marginTop="15dp"
            android:id="@+id/temperatura"
            android:inputType="numberDecimal|numberSigned"
            ></EditText>

    </LinearLayout>


</LinearLayout>
 
 
  ```


MainActivity.kt

```
package com.ingenieriajhr.termometroapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        termometro.tempMax(120f)
        termometro.tempMin(-50f)
        termometro.timeAnimation = 1000f

        mas.setOnClickListener {
            var temp = temperatura.text.toString()
            termometro.tempSet(temp.toFloat())
        }

        var a = 100f

        menos.setOnClickListener {
            a -=10f
            termometro.tempSet(a)
        }
    }

    override fun onWindowFocusChanged(hasFocus: Boolean) {
        super.onWindowFocusChanged(hasFocus)
        termometro.tempSet(10f)
    }

}
```


Gracias por usar mi libreria, Ingenieria JHR, si te gustaria apoyarme comunicate conmigo al 3107883975 WhatsApp
Suscribete a mi canal de youtube https://www.youtube.com/ingenieriajhr

