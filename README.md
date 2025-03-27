# Task 02: Stopwatch Web Application

## Project Overview

An interactive and user-friendly stopwatch web application that accurately measures and records time intervals. The application provides functionality for starting, pausing, and resetting the stopwatch, as well as tracking and displaying lap times.

## Features

- **Core Stopwatch Functions**
  - Start: Begin the timer with millisecond precision
  - Pause: Temporarily stop the timer while preserving the current time
  - Reset: Return the stopwatch to 00:00:00.00 and clear all lap records
  - Lap: Record split times while the stopwatch continues running

- **Time Display**
  - Hours, minutes, seconds, and milliseconds (centiseconds)
  - Leading zeros for consistent formatting
  - Visual indication when the timer is running

- **Lap Time Tracking**
  - Records and displays each lap time
  - Shows both the individual lap duration and total elapsed time
  - Newest laps appear at the top for better visibility
  - Scrollable container for viewing many lap times

- **Visual Design**
  - Color-coded buttons for intuitive use
  - Modern, clean interface
  - Responsive design for all device sizes
  - Subtle animations and transitions

## Technologies Used

- HTML5 for structure
- CSS3 for styling (flexbox, animations, custom properties)
- Vanilla JavaScript for timer functionality
- No external libraries or dependencies

## Implementation Details

### Timer Logic

The stopwatch uses `setInterval` for precise timing and calculates elapsed time based on the difference between the current time and start time:

```javascript
function startTimer() {
    if (!running) {
        startTime = Date.now() - elapsedTime;
        timerInterval = setInterval(function() {
            elapsedTime = Date.now() - startTime;
            updateDisplay(elapsedTime);
        }, 10);
        
        running = true;
        // Update UI state
    }
}
```

### Lap Time Recording

When a lap is recorded, the application calculates both the individual lap time and maintains the overall elapsed time:

```javascript
function recordLap() {
    if (running) {
        lapCount++;
        const currentLapTime = elapsedTime;
        const lapDuration = currentLapTime - lastLapTime;
        lastLapTime = currentLapTime;
        
        // Create and display lap record
    }
}
```

### Time Formatting

Time is formatted for display with proper leading zeros:

```javascript
function formatTime(time, digits = 2) {
    return time.toString().padStart(digits, '0');
}

function updateDisplay(timeInMilliseconds) {
    const hours = Math.floor(timeInMilliseconds / 3600000);
    const minutes = Math.floor((timeInMilliseconds % 3600000) / 60000);
    const seconds = Math.floor((timeInMilliseconds % 60000) / 1000);
    const milliseconds = Math.floor((timeInMilliseconds % 1000) / 10);
    
    // Update DOM elements with formatted time
}
```

## How to Use

1. Clone this repository
2. Open `index.html` in any modern web browser
3. Click "Start" to begin the stopwatch
4. Click "Lap" to record split times while the stopwatch continues running
5. Click "Pause" to temporarily stop the timer
6. Click "Reset" to clear the stopwatch and all recorded laps

## Responsive Design

The application is fully responsive and adapts to different screen sizes:

```css
@media screen and (max-width: 768px) {
    .stopwatch-container {
        padding: 1.5rem;
    }

    .timer-display {
        font-size: 3rem;
    }
    
    /* Additional responsive styles */
}

@media screen and (max-width: 480px) {
    .timer-display {
        font-size: 2.5rem;
    }
    
    /* Additional mobile styles */
}
```

## Future Enhancements

- Add countdown timer functionality
- Implement sound notifications
- Add ability to save and name timing sessions
- Export lap times to CSV or other formats
- Add custom themes/color schemes

## Screenshots


## License

This project is part of the SkillCraft Technology internship program.
