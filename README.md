#jadx-jitpack

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

Please note, that there might be a newer tag. Just check the newest available tag [here](https://jitpack.io/#fschrofner/jadx-jitpack) and replace `0.6.1-dev` by the newest tag name.  
If you'd like to use another build system, just check the link above as well.
