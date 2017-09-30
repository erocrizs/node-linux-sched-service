### XML Schedule Format

Add an XML file in this directory in the following format:

```xml
<schedule name="My Schedule">
    <task-group days="m-w-f">
        <task name="Do the laundry" time="8000-1000">
        </task>
        <task name="Work on Sched Service" time="1030-1130">
            <shell user="erocrizs">

                touch sample.log
                date >> sample.log
                cat sample.log
                rm sample.log
                echo "This is a test"
            </shell>
        </task>
    </task-group>
</schedule>
```


#### Schedule Tag (`<schedule>`)
Represents a weekly schedule. Must be the outermost tag. There should only be
one schedule tag inside an XML file.

```xml
<schedule name="schedule-name">
    ...
</schedule>
```

* `name`
    * Required.
    * Name of the schedule.


#### Task Group Tag (`<task-group>`)
Groups tasks together according to days of the week. Task groups must be direct
children of the schedule tag. There can be multiple task groups. Task groups
can have overlapping days (e.g. a task group is for M-W-F while another is
F-SA-SU).

```xml
<task-group days="m-w-f">
    ...
</task-group>
```

* `days`
    * Required.
    * Denotes which dates the tasks under the task group are active.
    * A string of codes to represent the days of the week, separated by "-".
    * Case insensitive.

| Days      | String Codes                  |
|-----------|-------------------------------|
| Monday    | m, mo, mon, monday            |
| Tuesday   | tu, tue, tues, tuesday        |
| Wednesday | w, we, wed, wednes, wednesday |
| Thursday  | th, thur, thurs, thursday     |
| Friday    | f, fr, fri, friday            |
| Saturday  | sa, sat, satur, saturday      |
| Sunday    | su, sun, sunday               |
| Daily     | daily                         |


#### Task Tag (`<task>`)
Represent a task or note that should fire a reminder on the proper time. Tasks
should be under the task group tag.

```xml
<task name="Do This" time="4pm-1700">
    ...
</task>
```

* `name`
    * Required.
    * Denotes the name of the task.
* `time`
    * Required.
    * Denotes the start and end time of the scheduled task.
    * Start and end time are separated by a "-".
    * Time can be expressed in regular time (e.g. 8am, 5:30pm) or 
    military time (e.g 0800, 1730).


#### Shell Tag (`<shell>`)
Optional tag within a task. This tag should enclose shell commands that should
be run when the time starts ticking. Each individual command must be written in
its own line.

```xml
<shell user="user" password="1234" directory="~/">
    command a
    command b
</shell>
```

* `root`
    * Required.
    * Name of the user that will run the command
* `password`
    * Optional.
    * Password of the user.
    * Default value is an empty string.
* `directory`
    * Optional.
    * The working directory in which the commands should be run.
    * Default value is the root directory.