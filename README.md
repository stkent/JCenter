# Usage

In your main `build.gradle` file, define the following extra properties:

```groovy
ext {
	// Library info:
	libraryVersion = '1.0.0'
	libraryName = 'Example'
	libraryGroupId = 'com.stkent.example'
	libraryArtifactId = 'example'
	libraryDescription = 'Exemplifying libraries since 2016.'
	libraryInceptionYear = '2016'
	libraryGitHubRepoName = 'stkent/Example'
	libraryGitHubUrl = "https://github.com/${libraryGitHubRepoName}"
	libraryIssueTrackerUrl = "${libraryGitHubUrl}/issues"
	libraryWebsiteUrl = libraryGitHubUrl
	libraryLabels = ['android']
	libraryLicenseName = 'Apache License Version 2.0'
	libraryLicenseUrl = 'http://www.apache.org/licenses/LICENSE-2.0.html'

	// Developer info:
	developerId = 'stkent'
	developerName = 'Stuart Kent'
	developerEmail = 'stkent@example.com'

	// Bintray categorization information:
	bintrayRepo = 'android-libraries'
}
```

Below this, add the following lines:

```groovy
apply from: 'bintray.gradle'
apply from: 'install.gradle'
```

You'll probably also want to set `android.defaultConfig.versionName` to `libraryVersion`:

```groovy
android {
  defaultConfig {
    versionName libraryVersion
  }
}
```

# Background Reading

http://inthecheesefactory.com/blog/how-to-upload-library-to-jcenter-maven-central-as-dependency/en
