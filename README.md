# youtube_auto_replay_custom

This is an easy and secure way to replay a custom part of a youtube video 🔥  !

In your browser Go to the Console in Developer Tools (usually accessible by pressing F12 or Ctrl+Shift+I in most browsers) then copy and paste the following javascript code :

```
(function startContinuousSegmentReplay() {
    const START_MINUTE = 1; // Start Minute
    const START_SECOND = 34; // Start Second
    const END_MINUTE = 2; // End Minute
    const END_SECOND = 33; // End Second

    const startTime = START_MINUTE * 60 + START_SECOND; // Total start time in seconds
    const endTime = END_MINUTE * 60 + END_SECOND; // Total end time in seconds

    // Function to replay the video from the specified segment
    function replaySegment() {
        const player = document.querySelector('video');
        if (player) {
            if (player.currentTime >= endTime) {
                player.currentTime = startTime; // Jump to start time if past end time
            }
            player.play(); // Play the video
        }
    }

    // Function to set up the event listener for the video
    function setupEventListener() {
        const player = document.querySelector('video');
        if (player) {
            player.addEventListener('timeupdate', replaySegment); // Check current time
            replaySegment(); // Start playing from the specified time immediately
        } else {
            console.error('Video element not found. Trying again in 1 second...');
            setTimeout(setupEventListener, 1000); // Retry after 1 second
        }
    }

    // Start the setup
    setupEventListener();
})();
```

Specify the start and end time for the part you want to replay and enjoy 🔥 !



