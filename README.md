# Creating an Exe File in Java

## 1. Clean and Build Your Project
Ensure your Java project is clean and successfully built. This can be done using your IDE's clean and build feature.

## 2. Organize Your Project Files
1. **Locate the Project Folder:** Navigate to your project folder.
2. **Dist Folder:** Within your project folder, find the `dist` folder. This folder typically contains the `.jar` file and any necessary libraries.
3. **Create a New Folder:** Create a new folder where you'll prepare the files for the .exe creation process.
4. **Copy Files:** Copy the `.jar` file and any dependencies (lib folder) from the `dist` folder to your new folder.

## 3. Download Necessary Tools
- **Launch4j:** Download and install Launch4j from [here](https://launch4j.sourceforge.net/). This tool will convert your `.jar` file into an `.exe` file.
- **NSIS (Nullsoft Scriptable Install System):** Download and install NSIS from [here](https://nsis.sourceforge.io/Download). This tool will create an installer for your application.

## 4. Prepare JRE
- **Obtain JRE:** Include the Java Runtime Environment (JRE) in your project folder. It's recommended to use the JRE rather than the JDK for distribution.

## 5. Configure Launch4j
1. **Open Launch4j:** Start Launch4j.
2. **Basic Tab:**
   - **Output file:** Choose the path in the new folder where the .exe file will be created.
   - **Jar:** Select the .jar file you copied earlier.
3. **Classpath Tab:**
   - **Custom classpath:** Check this option.
   - **Main class:** Specify the main class of your application (the class with the `main` method).
4. **Header:** No changes needed here.
5. **Single Instance:** Optionally, enable single instance and give a name for the instance.
6. **JRE Tab:**
   - Specify the JRE path if necessary. Ensure it points to the JRE included in your project.
7. **Environment Variables:** This step is optional.
8. **Splash:** Optional, you can choose to have a splash screen.
9. **Version Info:** Add version information if desired.
10. **Messages:** Optional, customize messages if necessary.
11. **Build:** Click the "Build wrapper" button to generate the .exe file.

## 6. Create Installer with NSIS
1. **Zip Files:** Zip the JRE, libraries, and the .exe file created by Launch4j.
2. **Open NSIS:** Start the NSIS compiler.
3. **Installer Script:**
   - Use NSIS script to create an installer for your application. Here’s a simple example of an NSIS script:

```nsis
OutFile "YourAppInstaller.exe"
InstallDir "$PROGRAMFILES\YourApp"
Page directory
Page instfiles
Section
  SetOutPath $INSTDIR
  File /r "path\to\your\zip\file\*.*"
SectionEnd
