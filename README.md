#jadx-jitpack [![](https://jitpack.io/v/fschrofner/jadx-jitpack.svg)](https://jitpack.io/#fschrofner/jadx-jitpack)

This is a fork of [jadx](https://github.com/skylot/jadx), which has received some slight modifications (removing unnecessary files, editing build.gradle, adding gradle wrapper) in order to be built with [jitpack's](https://jitpack.io/) build system.  

This has been done, since jadx does not provide a package on maven central. To use the jadx core library in your gradle project, simply add the jitpack repo:

```
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" }
	}
}
```

Then add this repository as dependency:
```
dependencies {
    compile 'com.github.fschrofner:jadx-jitpack:0.6.1-dev'
}
```

Please note, that there might be a newer tag. Just check the newest available tag [here](https://jitpack.io/#fschrofner/jadx-jitpack) (also shown next to the headline) and replace _0.6.1-dev_ by the newest tag name.  
If you'd like to use another build system, just check the link above as well.

####Using jadx without jitpack
If you want to use jadx without using the convenient method above, you can always just execute `./gradlew jar` in the _jadx-core_ directory to get a usable jar in the `build/libs` directory.  

To use this jar in your gradle project you'd need to copy it to your _libs_ folder and then add the following:

```
allprojects {
  repositories {
    flatDir {
      dirs 'libs'
    }
  }
}

dependencies {
    compile name: 'jadx-core-0.6.1-dev'
}
```

Of course the name needs to be changed to reflect the name of your .jar file.
