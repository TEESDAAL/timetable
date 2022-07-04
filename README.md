# Onslow Timetable
This is a timetable designed for a student who is studying at Onslow.

## Running the program
### Setup
 - Git clone this repository using the following url:`https://github.com/TEESDAAL/timetable`
 - Then install the node packages using npm install
```
git clone https://github.com/TEESDAAL/timetable
cd timetable
npm install
```
### - Running through the browser
1. run the web server by running `npm run dev` though the terminal

```
npm run dev
```
### - Running through the desktop app
1. cd into the src-tauri folder `cd src-tauri` then run `cargo build` **This will take a long time to compile!**
This timetable can be run through the desktop app using the following command in the command line
`npm run tauri dev`
**Note this will take a long time to compile the first time, and will also run the `npm run dev` command at the same time**
2. After a while the app should run on it's own opening the desktop app. - If this doesn't happen navigate to the `target -> debug -> app.exe` and run the app.exe file.
```
cd src-tauri
cargo build
npm run tauri dev
```
