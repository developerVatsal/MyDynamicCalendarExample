# MyDynamicCalendarLibrary
This is an Android Library for developer to use customized calendar with all type of views and features, like Month View, Week View, Day View, Agenda, Add Events, Add Holiday etc. So all of these features contain in one calendar.
<br>
Example is available in app module.

<p>
<img src="https://github.com/vatsaldesai92/MyDynamicCalendarLibrary/blob/master/app/src/main/assets/1.png" alt="screenshot" width="270">

<img src="https://github.com/vatsaldesai92/MyDynamicCalendarLibrary/blob/master/app/src/main/assets/2.png" alt="screenshot" width="270">

<img src="https://github.com/vatsaldesai92/MyDynamicCalendarLibrary/blob/master/app/src/main/assets/3.png" alt="screenshot" width="270">

<img src="https://github.com/vatsaldesai92/MyDynamicCalendarLibrary/blob/master/app/src/main/assets/4.png" alt="screenshot" width="270">
</p>

##Download

###Gradle dependency:
- Add the following to your project level build.gradle:
~~~
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" }
	}
}
~~~
- Add this to your app build.gradle:
~~~
dependencies {
	compile 'com.github.vatsaldesai92:MyDynamicCalendarLibrary:1.0.1'
}
~~~

<p>
<a href="https://play.google.com/store/apps/details?id=com.desai.vatsal.myamazingcalendar&hl=en">
<img src="https://github.com/vatsaldesai92/MyDynamicCalendarLibrary/blob/master/app/src/main/assets/google_play_icon.png" alt="screenshot" width="270">
</a>
</p>

##Usage

- Add MyDynamicRecyclerView in xml file or dynamicaly careate in java file.
~~~
    <com.desai.vatsal.mydynamiccalendar.MyDynamicCalendar
        android:id="@+id/myCalendar"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
	
	MyDynamicCalendar myCalendar = new MyDynamicCalendar(this);
~~~

- Design Calendar View
~~~
    myCalendar.setCalendarBackgroundColor("#eeeeee");	or	 myCalendar.setCalendarBackgroundColor(R.color.gray);
    myCalendar.setHeaderBackgroundColor("#454265");
    myCalendar.setHeaderTextColor("#ffffff");
    myCalendar.setNextPreviousIndicatorColor("#245675");
    myCalendar.setWeekDayLayoutBackgroundColor("#965471");
    myCalendar.setWeekDayLayoutTextColor("#246245");
    myCalendar.setExtraDatesOfMonthBackgroundColor("#324568");
    myCalendar.setExtraDatesOfMonthTextColor("#756325");
    myCalendar.setDatesOfMonthBackgroundColor("#145687");
    myCalendar.setDatesOfMonthTextColor("#745632");
    myCalendar.setCurrentDateBackgroundColor(R.color.black);
    myCalendar.setCurrentDateTextColor("#00e600");
    myCalendar.setBelowMonthEventTextColor("#425684");
    myCalendar.setBelowMonthEventDividerColor("#635478");
~~~

- Manage Saturday & Sunday
~~~
   // set all saturday off(Holiday) - default value is false
   // isSaturdayOff(true/false, date_background_color, date_text_color);
   myCalendar.isSaturdayOff(true, "#ffffff", "#ff0000");

   // set all sunday off(Holiday) - default value is false
   // isSundayOff(true/false, date_background_color, date_text_color);
   myCalendar.isSundayOff(true, "#ffffff", "#ff0000");
~~~

- Manage Events
~~~
    myCalendar.setEventCellBackgroundColor("#852365");
    myCalendar.setEventCellTextColor("#425684");

    // Add event  -  addEvent(event_date, event_start_time, event_end_time, event_title)
    myCalendar.addEvent("5-10-2016", "8:00", "8:15", "Today Event 1");
    myCalendar.addEvent("05-10-2016", "8:15", "8:30", "Today Event 2");
    myCalendar.addEvent("05-10-2016", "8:30", "8:45", "Today Event 3");

    // Get list of event with detail
    myCalendar.getEventList(new GetEventListListener() {
        @Override
        public void eventList(ArrayList<EventModel> eventList) {

        }
    });

    // updateEvent(position, event_date, event_start_time, event_end_time, event_title)
    myCalendar.updateEvent(0, "5-10-2016", "8:00", "8:15", "Today Event 111111");

    // Delete single event
    myCalendar.deleteEvent(2);

    // Delete all events
    myCalendar.deleteAllEvent();
~~~

- Manage Holiday
~~~
    myCalendar.setHolidayCellBackgroundColor("#654248");
    myCalendar.setHolidayCellTextColor("#d590bb");

    // set holiday date clickable true/false
    myCalendar.setHolidayCellClickable(false);

    // Add holiday  -  addHoliday(holiday_date)
    myCalendar.addHoliday("2-11-2016");
    myCalendar.addHoliday("13-11-2016");
    myCalendar.addHoliday("8-10-2016");
    myCalendar.addHoliday("10-12-2016");
~~~

- Navigate to particular date
~~~
    // setCalendarDate(date, month, year)
    myCalendar.setCalendarDate(5, 10, 2016);
~~~

- Month View
~~~
    // show month view
    myCalendar.showMonthView();

    // date click listener
    myCalendar.setOnDateClickListener(new OnDateClickListener() {
        @Override
        public void onClick(Date date) {

        }

        @Override
        public void onLongClick(Date date) {

        }
    });
~~~

- Month View With Event List (Show event on event date click)
~~~
    // show month view with events
    myCalendar.showMonthViewWithBelowEvents();

    // date click listener
    myCalendar.setOnDateClickListener(new OnDateClickListener() {
        @Override
        public void onClick(Date date) {

        }

        @Override
        public void onLongClick(Date date) {

        }
    });
~~~

- Week View
~~~
    // show week view
    myCalendar.showWeekView();

    // date click listener
    myCalendar.setOnDateClickListener(new OnDateClickListener() {
        @Override
        public void onClick(Date date) {

        }

        @Override
        public void onLongClick(Date date) {

        }
    });

    // week view blank cell click listener
    myCalendar.setOnWeekDayViewClickListener(new OnWeekDayViewClickListener() {
        @Override
        public void onClick(String date, String time) {

        }

        @Override
        public void onLongClick(String date, String time) {

        }
    });

    // single event cell click listener
    myCalendar.setOnEventClickListener(new OnEventClickListener() {
        @Override
        public void onClick() {

        }

        @Override
        public void onLongClick() {

        }
    });
~~~

- Day View
~~~
    // show day view
    myCalendar.showDayView();

    // day view blank cell click listener
    myCalendar.setOnWeekDayViewClickListener(new OnWeekDayViewClickListener() {
        @Override
        public void onClick(String date, String time) {

        }

        @Override
        public void onLongClick(String date, String time) {

        }
    });

    // single event cell click listener
    myCalendar.setOnEventClickListener(new OnEventClickListener() {
        @Override
        public void onClick() {

        }

        @Override
        public void onLongClick() {

        }
    });
~~~

- Agenda View
~~~
    // show agenda view
    myCalendar.showAgendaView();

    // date click listener
    myCalendar.setOnDateClickListener(new OnDateClickListener() {
        @Override
        public void onClick(Date date) {

        }

        @Override
        public void onLongClick(Date date) {

        }
    });
~~~


##License
~~~
    Apache Version 2.0

    Copyright 2016.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
~~~
