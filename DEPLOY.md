We have made certain changes to the POM files to allow uploading to our private servers. Specifically, `repositories` and `distributionManagement`.

Besides these changes, in order to publish from your system, you will need a configuration file in your `~/.m2/settings.xml` file. That is detailed below.

## Repository 
We are deploying to Typeset's public maven repository.

`s3://typeset-jrepo-public/snapshot/`

This is public readable but to push to it, you require access keys which can be obtained from the aws console.

## Maven settings

Put this in your `~/.m2/settings.xml`
```xml
<settings>
  <servers>
    <server>
      <id>s3-release-repo</id>
      <username>ACCESS_KEY_ID</username>
      <password>SECRET_KEY</password>
    </server>
    <server>
      <id>s3-snapshot-repo</id>
      <username>ACCESS_KEY_ID</username>
      <password>SECRET_KEY</password>
    </server>
  </servers>
</settings>
```

## Deploying

As simple as `mvn clean deploy`