# Onslow Timetable
This is a timetable designed for a student who is studying at Onslow.

## Running the program
This app can be used in two ways.
### 1. Through the browser
This timetable can be run through the browser using the following command in the command line
`npm run dev`
### 2. Through the desktop app
1. run `npm install` in the terminal from the root directory of the project
2. cd into the src-tauri folder `cd src-tauri` then run `cargo build` **This will take a long time to compile!**
This timetable can be run through the desktop app using the following command in the command line
`npm run tauri dev`
**Note this will take a long time to compile the first time, and will also run the `npm run dev` command at the same time**
3. After a while the app should run on it's own opening the desktop app. - If this doesn't happen navigate to the `target -> debug -> app.exe` and run the app.exe file.