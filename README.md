# Alarm Clock GUI (Java + Swing + MySQL)

This is a full-featured Alarm Clock application built using **Java Swing** for the graphical interface and **MySQL** for storing alarm data persistently. It allows users to set multiple alarms, which ring at the specified date and time. The application also shows the current system time and offers a professional UI experience.

---

## 🧰 Features

* ✅ Real-time clock display (12-hour format with AM/PM)
* ⏰ Add, list, and remove alarms
* 🔔 Custom sound notification for alarms
* 💾 Persistent alarm storage using MySQL database
* 🧠 Smart alarm validation (no duplicates or past alarms)
* 🎨 Intuitive and stylish GUI

---

## 📂 Project Structure

```
AlarmClockGUI.java       # Main class with full GUI and functionality
README.md                # Project documentation
```

---

## 🚀 Getting Started

### 🔧 Prerequisites

* Java JDK 8 or higher
* MySQL Server installed and running
* Java IDE (e.g., IntelliJ IDEA, Eclipse)

---

### 🗃️ Database Setup

Create a MySQL database and `alarms` table:

```sql
CREATE DATABASE alarmdb;

USE alarmdb;

CREATE TABLE alarms (
  id INT AUTO_INCREMENT PRIMARY KEY,
  alarm_time DATETIME NOT NULL
);
CREATE DATABASE alarmdb;

use alarmdb;

CREATE TABLE alarms (
    id INT AUTO_INCREMENT PRIMARY KEY,
    alarm_date DATE,
    alarm_time TIME,
    am_pm VARCHAR(2)
);

select * from alarms;
```

Edit the database connection credentials inside the code if needed:

```java
String url = "jdbc:mysql://localhost:3306/alarmdb?useSSL=false&serverTimezone=UTC";
String user = "root";
String password = "root";
```

---

### ▶️ Run the Application

1. Clone the repository or copy the code.
2. Open it in your preferred Java IDE.
3. Make sure MySQL server is running.
4. Run `AlarmClockGUI.java`.

---

## 🖥️ Usage Instructions

1. **Check Current Time:** The top label displays the current time.
2. **Set Alarm:**

   * Choose a date, hour, and minute.
   * Select AM/PM.
   * Click `Add Alarm`.
3. **View Alarms:** Alarms appear in the list.
4. **Remove Alarm:** Select an alarm and click `Remove Selected`.
5. When the alarm time is reached, a dialog will show and a sound will play.

---

## 🔊 Alarm Sound

* The alarm generates a sine wave tone of **1000 Hz** with a duration of **3 seconds**.
* This can be customized in the `prepareAudioClip()` method.

To customize frequency:

```java
float desiredFreq = 880f; // Change to any audible frequency
```

---

## 🛠️ Customization

* 🎵 To use a custom audio file, you can replace `prepareAudioClip()` with:

```java
AudioInputStream audioIn = AudioSystem.getAudioInputStream(new File("alarm.wav"));
clip = AudioSystem.getClip();
clip.open(audioIn);
```

* 🎨 Modify colors and font in the UI via the Swing component properties.

---

## 🧪 Testing

* Try adding past dates to check validation.
* Add same alarm time to see duplicate prevention.
* Run app, close and re-open to test DB persistence (if you later load alarms from DB).

---

## 📦 Dependencies

* Java Swing (Standard)
* Java Sound API (Standard)
* JDBC (Java Database Connectivity)

---

## 🙋 FAQ

**Q: What happens if MySQL is not running?**
A: The app will show a console error but still work (without saving alarms).

**Q: Can I disable sound?**
A: You can comment out or modify the `playAlarmSound()` method.



Enjoy building and improving your productivity with this Alarm Clock! ⏰✨
