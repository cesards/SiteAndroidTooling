
Lint checks 

To enable these checks, go to File > Preferences > Editor > Inspections and check the rules that you want to 
enable under Kotlin Interoperability:

Once you have checked the rules you would like to enable, the new checks will run when you run your 
code inspections (Analyze > Inspect Code…)
 To enable these checks from the command-line builds, add the following line in your build.gradle file:

 CHECK gradle plugins section:
 android {
    lintOptions {
        check 'Interoperability'
    }
}



FOR TOOL ATTRIBUTE LINT STUFF, link to the right section here.