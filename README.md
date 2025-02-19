# Purpose

It used to be possible to download workshop maps without having to run pavlov, because Steam downloaded those when you were subscribed.

This is no longer possible and Pavlov VR does not seem to automatically download maps that you subscribed to on Mod.io.

Since not everybody has a great internet connection to be able to download any map during mapchange, it is necessary to have the means to download and update all maps without having to keep the game running.

This tool will download and update your subscribed Mod.io Pavlov VR mods and also existing mods you have already downloaded.

# Usage

Make sure you have [.net 6](https://aka.ms/dotnet-core-applaunch?missing_runtime=true&arch=x64&rid=win10-x64&apphost_version=6.0.22) installed.  
To run the program, simply [download](https://github.com/RainOrigami/DownloadPavlovMapsFromModIo/releases/latest/download/DownloadPavlovMapsFromModIo.exe) and execute.

## Startup parameters

There are two startup parameters you can provide to the program:
- `--yes` - Will skip all confirmation messages and answer them with "yes" automatically for automating the whole download process
- `--subscribedonly` - Will only check for and download subscribed mods instead of also including all existing mods that are not subscribed

## First time setup

At first start you will be prompted for your Mod.io OAuth Access Token and your Pavlov VR Mods folder.

To generate an OAuth Access Token:
1. Go to https://mod.io/me/access
2. Under OAuth Access, enter any name (eg. Pavlov) and press Create
3. Now enter any name for the token (eg. Pavlov), choose Read from the dropdown, and press the + button
4. "TOKEN CREATED" will appear and you can copy that token using the copy button on the left side of the text field

The Pavlov VR Mods folder should be detected automatically. If it is unable to do so you will have to supply the correct path. If the path is correct, press `y` and `Enter` to confirm and continue.

These settings are saved into a `settings.json` file. If your OAuth Access Token ever expires or you need to change the Pavlov VR Mods folder path, you can either edit the file directly or simply remove it to go through the first time setup again.

## Downloading and updating

Subscribe to all mods on Mod.io that you want to download and update. Existing mods that you have already downloaded but are not subscribed to are also updated, this can be prevented using the `--subscribedonly` startup argument.

These mods are then listed with their respective required action (new, update, up to date).

Press `y` and `Enter` to confirm these actions. The download will begin and you will see the progress of the download for each mod. You can disable having to confirm by using the `--yes` startup argument.

After all mods are downloaded, press any key to exit the program.

![image](https://github.com/RainOrigami/DownloadPavlovMapsFromModIo/assets/51454971/c027606d-b899-4a7d-bf3d-2acacb05e699)

# Errors

## Program does not start

Make sure you have [.net 6](https://aka.ms/dotnet-core-applaunch?missing_runtime=true&arch=x64&rid=win10-x64&apphost_version=6.0.22) installed.  
You may have to start the program in a command line window to get its error message output.

https://github.com/RainOrigami/DownloadPavlovMapsFromModIo/assets/51454971/21a1973b-4883-49a8-b9af-2951d8000a99

## Yellow text in console output

Yellow means warning, the program is usually able to continue however there may be something unexpected happening (eg. trying to update a mod that does not exist on mod.io anymore).  
It is recommended but not required to check and solve the cause, however these are not errors but simply warnings and can be ignored.

## Red text in console output

Red means error, the program is not likely to be able to continue.  
You will have to solve the error for the program to function properly.

## Access token is very short

The correct OAuth access token is over 1000 characters long. If your access token is too short, you probably copied the API key instead. Make sure to follow the first time setup guide on how to generate an OAuth Access Token.

## Failed to get user data from Mod.io. Make sure your token is correct and has read permissions.

The supplied token did not allow for access to your Mod.io profile. Either your token is incorrect (make sure, if you paste it, to not add any additional characters such as spaces) or you have set it to write permissions, instead of read permissions.

## Could not find Pavlov VR mods directory

Usually Pavlov stores the mods in `%localappdata%\Pavlov\Saved\Mods`. If this directory was not found, you either do not have Pavlov installed, never started it, or changed ModDirectory in your GameUserSettings.ini to store your mods somewhere else.
Either install and start Pavlov at least once before running the tool to properly autodetect the directory, or supply the correct path yourself.

## Failed to get subscribed mods from Mod.io

The OAuth Access Token you supplied during first time setup has expired. You have to generate a new one. You can either replace the token in `settings.json` or simply delete `settings.json` and redo the first time setup.

## Failed to extract Pavlov VR mods from subscribed mods

The data received from Mod.io about your subscribed mods is corrupt in some way. Contact us by creating a [new issue](https://github.com/RainOrigami/DownloadPavlovMapsFromModIo/issues).

## No Pavlov VR mods found

This simply means that you did not subscribe to any mods on Mod.io.

## Could not find a Windows version of this mod. Skipping.

The creator of this mod has not made it available on Windows.

## Any other errors

Contact us by creating a [new issue](https://github.com/RainOrigami/DownloadPavlovMapsFromModIo/issues)
