# OneCalendarView
CalendarView Personalizado para desarrolladores android
OneCalendarView es un CalendarView Personalizado que perimite a los desarrolladores android tener el mismo CalendarView en cualquier aplicacion android (API 16 o superior).

#Live Demo app
usted puede ver una aplicacion demo en el siguiente enlace https://appetize.io/app/cymqjzvzaybypepxhnmn4hewx0

#Instalación
en su archivo /app/build.gradle
```
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
       compile 'com.github.MorochoRochaDarwin:OneCalendarView:3.0.0'
}
```

#Agregar la vista OneCalendarView a su Layout
```xml
  <com.darwindeveloper.onecalendar.views.OneCalendarView
        android:id="@+id/oneCalendar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        />
```
#En sus Actividades o Fragments
Inicialice la vista y llame a sus 2 metodos obligatorios para capturar los eventos en el calendario (NOTA: de no llamar a estos metodos se producira un error en tiempo de ejecución).

```java
protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        final OneCalendarView calendarView = (OneCalendarView) findViewById(R.id.oneCalendar);



        //el siguiente fragmento puede ser usado para capturar los swipes en el calendar
        calendarView.setOnCalendarChangeListener(new OneCalendarView.OnCalendarChangeListener() {

            /**
             * notifica al usuario que el calendario a cambiado al mes anterior
             */
            @Override
            public void prevMonth() {
                //hacer algo aqui
            }

            /**
             * notifica al usuario que el calendario a cambiado al mes siguiente
             */
            @Override
            public void nextMonth() {
                //hacer algo aqui
            }
        });


        //el siguiente fragmento de codigo muestra como obtener los datos de un dia en el calendario
        //ademas de realizar otras acciones
        calendarView.setOneCalendarClickListener(new OneCalendarView.OneCalendarClickListener() {

            /**
             * cuando se da click en un dia en el calendario mostrado
             *
             * @param day      un Objeto de tipo Day del cual podemos llara a su metodo getDate() para recuperar una fecha
             * @param position posicion desde 0-41, que ocupa en el calendario actual
             */
            @Override
            public void dateOnClick(Day day, int position) {
                //recuerde que en java los meses inician desde 0
            }

            /**
             * cuando se da click prolongado en un dia en el calendario mostrado
             *
             * @param day      un Objeto de tipo Day del cual podemos llara a su metodo getDate() para recuperar una fecha
             * @param position posicion desde 0-41, que ocupa en el calendario actual
             */
            @Override
            public void dateOnLongClick(Day day, int position) {

            }
        });

    }
```

También puede llamar a los dos metodos anterioes implementando las interfaces OneCalendarView.OnCalendarChangeListener y OneCalendarView.OneCalendarClickListener
```java
calendarView.setOnCalendarChangeListener(this);
calendarView.setOneCalendarClickListener(this); 
```

#Diseño completo
Usted puede agregar varios atributos a la vista en sus layouts y crear diseños unicos. A continuación un ejemplo completo
```xml
 <com.darwindeveloper.onecalendar.views.OneCalendarView
        android:id="@+id/oneCalendar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:backgroundColorDaysOfAnotherMonth="@color/colorPrimary"
        app:backgroundColorDaysOfMonth="#53c0c0c1"
        app:backgroundColorSelectedDay="#d2d2d2"
        app:calendarBackgroundColor="@color/colorPrimary"
        app:calendarLanguage="EN"
        app:currentDayBackgroundColor="#fad501"
        app:mainBackgroundColor="@color/colorPrimary"
        app:textColorDaysOfAnotherMonth="#fff"
        app:textColorDaysOfMonth="#fff"
        app:textColorMonthAndYear="@color/colorPrimary"
        app:textColorSelectedDay="#000000" />
```



