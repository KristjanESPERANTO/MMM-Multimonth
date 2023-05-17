### NOTE: THIS MODULE IS TO BE HOSTED ONLY AT https://github.com/BKeyport/MMM-Multimonth - Any other hosting location is invalid.

If you fork and change any code, please let me know, if it's useful for the general public, I'd love to add it!

If you find this module useful, and would like to contribute to the project, I appreciate the thought. Instead of giving to me, please donate to L'Arche Tahoma Hope
at https://www.larchetahomahope.org/donate/ - in honor of Nancy Tyson. (Dedicate my donation checkbox). Nancy means the world to me. You don't have to notify me you
have done so.

THANK YOU for your consideration.

# MagicMirror Module to display a calendar with multiple months (user configurable)

This is a module for the [MagicMirror](https://github.com/MichMich/MagicMirror) project.

This will create a mini-calendar with as many months as the user wants, assuming screen space is available. Screenshots are with config examples.

## Installation

Clone this repository in your ~/MagicMirror/modules/ folder ( $ cd ~MagicMirror/modules/ ):

git clone https://github.com/BKeyport/MMM-Multimonth.git

** note: NPM INSTALL is no longer required. This module is proud to no longer use any external dependencies! **

## Using the module

To use this module, add it to the modules array in the config/config.js file - shown options are defaults:

```
{
  module: 'MMM-Multimonth',
    position: 'top_left', // can be any of the postions
    config: { // Optional - will default to 3 months, with one previous and one next, vertical orientation.
    }
},
```
** Full config options: **

| Option                                              | Default | Description                                                         |
|-:|:-:|-|
| startMonth                                          | -1      | Starting month relative to the current month                        |
| monthCount                                          | 3       | How many months do you want to display?                             |
| monthsVertical                                      | false   | Display months on a vertical line                                   |
| repeatWeekdaysVertical                              | false   | Repeat the weekday names? <br> (Vertical Calendar Only)             |
| weekNumbers                                         | false   | Show the week numbers (How many weeks in the year)                  |
| weekNumbersISO                                      | false   | Use ISO calculation or US/CA calculation (ignored if WeekNumbers is false) |
| highlightWeekend                                    | false   | highlight the weekend (See Below)                                   |
| headerType                                          | 'short' | How do you want the days displayed?<br>In US - 'short' = "Sun, Mon, Tue"<br>In US - 'narrow' = "S, M, T"|
| otherMonths                                         | false   | Display the previous and next month dimmed in the month grid.       |
| eventsOn                                            | true    | Turn on and off Event monitoring                                    |
| calNames                                            | []      | List of calendar names to trigger underline. Empty will do all of them. |
| startWeek                                           | 0       | Starting day of your week                                           |
| weekend1                                            | 0       | 1st Day of your weekend                                             |
| weekend2                                            | 6       | 2nd day of your weekend                                             |


for the last three items: 0 = Sunday, 1 = Monday, 2 = Tuesday, 3 = Wednesday, 4 = Thursday, 5 = Friday, 6 = Saturday.
Remember the format for options:

```option: value,``` Example: ``` startMonth: -1, ```

Important: calNames is an array, please specify as such ```["Main", "Sportsball", "Utility"]``` case is IMPORTANT. 

To get events to feed to module, add the calendar module into your ```config.js```

Suggested settings at minimum: (name for other modules that use this calendar data) 
```
		{
			module: "calendar",
			config: {
				broadcastPastEvents: true,
				calendars: [
					{
						url: <insert URL>,
						name: <name>,
					},
					//.... As many as you'd like .... 
				],
			}
		},
```


Updating from prior to 11 Nov 2022: 

CSS is changed - please remove all old customizations in custom.css and reset to new: 

The following CSS code is all you need in ```custom.css``` if all you're changing is the colors and/or background edge rounding: 

```
.MMM-Multimonth .settings {
  --background-dimmed: var(--color-background);     /* For dimmed (previous/next month in current grid), use the global background color */
  --background-weekday: var(--color-background);    /* For normal days, use global background */ 
  --background-weekend: cornflowerblue;             /* For the days defined as your weekend, change the background to cornflowerblue */
  --background-current: Yellow;                     /* for the current day, change the background to yellow */ 
  --background-header: Green;                       /* for the month and year line, use green background */ 
  --background-weekno: grey;                        /* for the week number, use a grey background */ 
  --background-dow: var(--color-background);        /* For the days of the week, use global background */ 
  --color-weekday: var(--color-text);               /* For normal days, use global normal text */ 
  --color-weekend: var(--color-background);         /* For the days defined as your weekend, change the text to the background color */
  --color-current: var(--color-background);         /* for the current day, change the text to the background color */ 
  --color-dimmed: var(--color-text-dimmed);         /* For dimmed (previous/next month in current grid), use the global dimmed text color */
  --color-header: var(--color-text-bright);         /* for the header lines, use the global bright text color */ 
  --color-weekno: var(--color-text-bright);         /* for the week numbers, use the global bright text color */
  --color-dow: var(--color-text);                   /* for the days of the week header, use the global text color */
  --color-event: Red;                               /* For events, the color of the underline */
  --back-rounding: 8px;                             /* Set the radius of the background rounded edges. See documentation for border-radius elsewhere */ 
  --alignment: center;                              /* Adjust the text alignment */ 
}
```


| Screenshot                                                                                                                     | How to get                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| ![screenshot](vert-noweek-norep.png?raw=true "Screenshot (vertical mode, no week numbers, single weekday line)")               | monthsVertical: true, <br> repeatWeekdaysVertical: false, <br> weekNumbers: false, |
| ![screenshot](vert-noweek-rep.png?raw=true "Screenshot (vertical mode, no week numbers, repeat weekday line for every month)") | monthsVertical: true, <br> repeatWeekdaysVertical: true, <br> weekNumbers: false,  |
| ![screenshot](vert-week-norep.png?raw=true "Screenshot (vertical mode, no week numbers, single weekday line)")                 | monthsVertical: true, <br> repeatWeekdaysVertical: false, <br> weekNumbers: true,  |
| ![screenshot](vert-week-rep.png?raw=true "Screenshot (vertical mode, no week numbers, repeat weekday line for every month)")   | monthsVertical: true, <br> repeatWeekdaysVertical: true, <br> weekNumbers: true,   |
| ![screenshot](horz-noweeknum.png?raw=true "Screenshot (horizontal mode)")                                                      | monthsVertical: false, <br> weekNumbers: false,                                    |
| ![screenshot](horz-week.png?raw=true "Screenshot (horizontal mode)")                                                           | monthsVertical: false, <br> weekNumbers: true,                                     |

Many thanks to kirash for the inspiration with the monthly_calendar module, sdetweil and lavolp3 for the help in coding and CSS work. Without your help, this would just be a pipe dream.

Please, if you have any suggestions for improvement, let me know, I'm learning JS and CSS as I write this, and I dream of much bigger things.

Language Localization is controlled by the master language of MagicMirror. 

## Versioning

0.1 - Initial Release

0.2 - Change code to improve functionality, allow for some localization - will not move start of week yet, but will change languages with system.

0.25 - Fix code with temporary bodge so to refresh every hour to assure day changes sometime between midnight and 1 am.

0.3 - Removed bodge in 0.25, replaced with a simple refresh at midnight, no animation, as I find it annoying.

0.9 - Start of week now moves per moment.js. Note: at this point, module is almost everything I wanted. If I don't get any bug reports that I can control, I'm going to bump it up to 1.0 and call it good.

0.95 - Fix start of week issue. Had a calculation backwards. - Suggestion was made to optionally add week numbers to the system, still working on that.

0.99 - Major rewrite by [Volker Wegert](https://github.com/vwegert) (Danke sehr!) - Implements everything I want, and I even understand the wizard level code he wrote.

1.00 - Minor changes to code/css to standardize look.

1.10 - Added leading and trailing months when 1 month is selected per user request.

1.20 - Added weekend highlight, default is off.

1.21 - Added weekend highlight for current day, so user could specify a different look for current day on weekend.

1.50 - Minor fixes

1.90 - Minor fixes/Remove EOL - Begin work on moving to a life without moment.js - Goal, no dependencies.

7 Sep 2022 -    changing to date based versioning.

1 Oct 2022 -    Completely removed moment.js from project. ** Returned to Beta Status due to lack of internationalization and start of week adjustments ** 

4 Oct 2022 -    Internationalization and Start of Week added back in. -- Note: I'm aware of a bug where the week numbers are showing an extra week. I'm redesigning the layout. 

5 Oct 2022 -    Fix bug in week numbers, fix extra week error.

12 Oct 2022 -   Fix bug causing last day of month to fall off calendar if it's the same day as start of week. 

24 Oct 2022 -   Add config option for previous/next month display rather than forcing based on use. 

29 Oct 2022 -   Start Implementing streamlined CSS, add feature to move weekend around, documentation improvements. 

4 Nov 2022 -    Correct US/CA Week number calculation, add ISO calculation. 

11 Nov 2022 -   Changes: 
* Temporary disabled US/CA week numbers, routine isn't consistent. I'm gonna rework it. Regardless of how it's set, you will use ISO week numbers.
* Rewrote javascript to match new knowledge, saving several lines of code and making more CSS sense. 
* added classes for future features, prepped more things for major future planned feature. 
* Streamlined CSS classes some more. 
* Due to changes, css class "current_day_weekend" is no longer supported. It does nothing. 

26 Nov 2022 -   Changes: 
* Added support for events from default calendar module. 
* Changed the following css elements: day, dim, weekend, current, event, settings. 
* Added new varable "--color-event" - which sets the color of the underline marking event on that day. 

28 Nov 2022 - Added config option "eventsOn" to control event monitoring. 

17 May 2023 - Added calNames - a way to control which calendars do what. Please see above.
