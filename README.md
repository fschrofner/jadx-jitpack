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
    compile 'com.github.fschrofner:jadx-jitpack:0.6.1'
}
```

Please note, that there might be a newer tag. Just check the newest available tag [here](https://jitpack.io/#fschrofner/jadx-jitpack) (also shown next to the headline) and replace _0.6.1_ by the newest tag name.  
If you'd like to use another build system, just check the link above as well.

####Logback
Jadx uses (and requires) logback to run, so you need to include that in your project. I decided to strip the dependency from the lib itself, as it would make it hard to do any logging in your project as both logging libraries interfere.

So if you stumble upon an error that has anything to do with logging, make sure that you included the following (or another logback version) in your build.gradle.

```
dependencies {
    compile 'ch.qos.logback:logback-classic:1.1.7'
}
```

If you then want to prevent jadx from logging anything, create a file at `src/main/resources/logback.groovy` with the following contents.

```
root(OFF, [])
```
After that you should be good to go.

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
    compile name: 'jadx-core-0.6.1'
}
```

Of course the name needs to be changed to reflect the name of your .jar file.
