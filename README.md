# myTimer 🍅

A flexible, command-line Pomodoro-style focus timer for macOS, designed for developers, writers, and anyone looking to manage their work and break intervals effectively.

This tool can control system volume, pause and play Apple Music, or launch a YouTube video to provide an audio backdrop for your focus sessions. It's built with Node.js and is highly configurable through simple command-line flags.

## Features

  * **Three Operating Modes:**
      * **System Mute Mode:** Mutes and unmutes the system volume for silent, focused work.
      * **Apple Music Mode:** Controls the Music app by playing a specific playlist, then pausing for breaks and resuming for work. Can search the Apple Music catalog if a playlist isn't in your local library.
      * **YouTube Mode:** Launches a specified YouTube URL in your default browser at the start of a session.
  * **Fully Configurable Intervals:** Customize the duration of work intervals, break intervals, and the total number of cycles using simple command-line flags.
  * **Intelligent Logic:**
      * Saves and restores your original system volume instead of just muting/unmuting.
      * Gracefully exits with a clear error message if a specified local Apple Music playlist is not found.
      * Skips the final, redundant break by default to end your session cleanly.
  * **User-Friendly Notifications:**
      * Provides timestamped status updates in the terminal.
      * Plays a series of audible beeps when the entire focus session is complete.

## Installation

This project is built on Node.js and is designed for macOS.

1.  **Prerequisites:** Ensure you have [Node.js](https://nodejs.org/) installed on your system. Using a version manager like [NVM](https://github.com/nvm-sh/nvm) is recommended.
2.  **Clone or Download:** Get the project files onto your local machine.
3.  **Install Dependencies:** Open your terminal, navigate to the project directory (`myTimer`), and install the necessary packages.
    ```bash
    npm install
    ```
4.  **Make it Executable:** Grant the main script executable permissions.
    ```bash
    chmod +x myTimer
    ```
5.  **Create Global Command (Recommended):** To run the `myTimer` command from any directory, link the package.
    ```bash
    npm link
    ```

## Usage

Once linked, you can call `myTimer` directly from your terminal. Here are some examples for the different modes.

#### System Mute Mode

This is the default mode. It's perfect for focused work where you want any background audio to be silenced during breaks.

  * **Run a standard session (4 cycles of 25 min work / 5 min break):**
    ```bash
    myTimer
    ```
  * **Run a "deep work" session (2 cycles of 50 min work / 10 min break):**
    ```bash
    myTimer -w 50 -b 10 -i 2
    ```

#### Apple Music Mode

This mode controls the Music app. Specify a playlist to begin your session.

  * **Play a playlist from your library:**
    ```bash
    myTimer --playlist "Deep Focus"
    ```
  * **Search the Apple Music catalog if the playlist isn't in your library:**
    ```bash
    myTimer --playlist "Lofi Beats" --search
    ```

#### YouTube Mode

This mode launches a YouTube video for background music or ambience.

  * **Start a session with a YouTube video:**
    ```bash
    myTimer "https://www.youtube.com/watch?v=jfKfPfyJRdk"
    ```

## Command-Line Options

| Flag | Alias | Description | Default |
| :--- | :---: | :--- | :---: |
| `--work` | `-w` | Duration of work intervals in minutes. | `25` |
| `--break`| `-b` | Duration of break intervals in minutes. | `5` |
| `--interval`| `-i` | The number of work/break cycles to run. | `4` |
| `--playlist`|  | The name of an Apple Music playlist to play. | `N/A` |
| `--search` | | If a local playlist isn't found, search the Apple Music catalog. | `false` |
| `--last-break`| | Include the final break period after the last work interval. | `false` |
| `--help` | `-h` | Show the help message. | `N/A` |
