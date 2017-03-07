# Goal

Simplify configuration of the [Bintray](https://github.com/bintray/gradle-bintray-plugin), [Android Maven](https://github.com/dcendents/android-maven-gradle-plugin), and [license](https://github.com/hierynomus/license-gradle-plugin) Gradle plugins for Android library projects.

# Usage

1. Add the following items to your `build.gradle`'s `buildscript` block:

	```groovy
	buildscript {
	    repositories {
	        jcenter()
	    }
	
	    dependencies {
	        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:{bintray-version}'
	        classpath 'com.github.dcendents:android-maven-gradle-plugin:{install-version}'
	    }
	}
	```
	
2. Apply the license plugin (no additional configuration needed):

	```groovy
	plugins {
	    id "com.github.hierynomus.license" version "{license-version}"
	}
	
	apply from: 'https://raw.githubusercontent.com/stkent/JCenter/master/license{license-version}.gradle'
	```

2. Define the following extra properties, to be shared by the Bintray and Android Maven plugins:

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

3. Apply the Bintray and Android Maven plugins **below** the extra properties defined above:

	```groovy
	apply from: 'https://raw.githubusercontent.com/stkent/JCenter/master/bintray{bintray-version}.gradle'
	apply from: 'https://raw.githubusercontent.com/stkent/JCenter/master/install{install-version}.gradle'
	```

4. (Optional) You'll probably also want to set `android.defaultConfig.versionName` to `libraryVersion` for consistency:

	```groovy
	android {
	  defaultConfig {
	    versionName libraryVersion
	  }
	}
	```

# Background Reading

http://inthecheesefactory.com/blog/how-to-upload-library-to-jcenter-maven-central-as-dependency/en
