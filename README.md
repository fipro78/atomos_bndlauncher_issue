# Atomos Bnd Launcher Issue Reproducer

This repository contains a minimal reproducer for issue https://github.com/bndtools/bnd/issues/5243

- Build the app via `mvn clean verify`
- Try to run the atomos variant via `java -jar org.fipro.service.app/target/atomos-equinox-app.jar`

This produces an exception like this: 

```
org.osgi.framework.BundleException: Error reading bundle content.
        at org.eclipse.osgi.storage.Storage.getContentConnection(Storage.java:623)
        at org.eclipse.osgi.storage.Storage.install(Storage.java:667)
        at aQute.launcher.pre.EmbeddedLauncher.executeWithRunPath(EmbeddedLauncher.java:170)
        at aQute.launcher.pre.EmbeddedLauncher.findAndExecute(EmbeddedLauncher.java:119)
        at aQute.launcher.pre.EmbeddedLauncher.main(EmbeddedLauncher.java:52)
Caused by: java.net.MalformedURLException: no protocol: jar/org.apache.felix.gogo.command-1.1.2.jar
        at java.base/java.net.URL.<init>(URL.java:674)
        at java.base/java.net.URL.<init>(URL.java:569)
        at java.base/java.net.URL.<init>(URL.java:516)
        at org.eclipse.osgi.storage.Storage.createURL(Storage.java:663)
        at org.eclipse.osgi.storage.Storage.getContentConnection(Storage.java:648)
        at org.eclipse.osgi.storage.Storage.getContentConnection(Storage.java:619)
        ... 12 more
```