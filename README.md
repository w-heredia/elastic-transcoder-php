Elastic Transcoder PHP Class
====================

PHP class for interacting with Amazon Elastic Transcoder that does not require PEAR.

#### Usage ###

Object-oriented method:

```php
$et = new ElasticTranscoder($awsAccessKey, $awsSecretKey, $awsRegion);
```

Statically:

```php
ElasticTranscoder::setAuth($awsAccessKey, $awsSecretKey, $awsRegion);
```

<strong>Note:</strong> us-east-1 is the default AWS region setting. The third parameter is optional for us-east-1 users.

#### Job Operations ####

Creating a transcoding job:

```php
$pipelineId = 'pipelineId';
$input = array('Key' => 'inputFile');
$output = array(
  'Key' => 'outputFile.mp4',
  'PresetId' => 'presetId'
 );

$result = ElasticTranscoder::createJob($input, array($output), $pipelineId);

if (!$result) {
  echo ElasticTranscoder::getErrorMsg();
} else {
  echo 'New job ID: ' . $result['Job']['Id'];
}
```

List jobs by pipeline:

```php
ElasticTranscoder::listJobsByPipeline( string $pipelineId [, boolean $ascending = true ] );
```

List jobs by status:

```php
ElasticTranscoder::listJobsByStatus( string $status );
```

Get job info:

```php
ElasticTranscoder::readJob( string $jobId );
```

Cancel a job:

```php
ElasticTranscoder::cancelJob( string $jobId );
```

#### Pipeline Operations ####

Create a new pipeline:

```php
ElasticTranscoder::createPipeline( string $name, string $inputBucket, string $outputBucket, string $role [, array $notifications ] );
```

Get a list pipelines:

```php
ElasticTranscoder::listPipelines();
```

Get info about a pipeline:

```php
ElasticTranscoder::readPipeline( string $pipelineId );
```

Update pipeline settings:

```php
ElasticTranscoder::updatePipeline( string $pipelineId, array $updates );
```

Change the status of a pipeline (active/paused):

```php
ElasticTranscoder::updatePipelineStatus( string $pipelineId, string $status );
```

Update pipeline notification settings:

```php
ElasticTranscoder::updatePipelineNotifications( string $pipelineId [, array $notifications ] );
```

Delete a pipeline:

```php
ElasticTranscoder::deletePipeline( string $pipelineId );
```

Test the settings for a pipeline:

```php
ElasticTranscoder::testRole( string $inputBucket, string $outputBucket, string $role, array $topics );
```

#### Preset Operations ####

Create a preset:

```php
ElasticTranscoder::createPreset( array $options );
```

List all presets:

```php
ElasticTranscoder::listPresets();
```

Get info about a preset:

```php
ElasticTranscoder::readPreset( string $presetId );
```

Delete a preset:

```php
ElasticTranscoder::deletePreset( string $presetId );
```

#### Misc. ####

Set AWS authentication credentials:

```php
ElasticTranscoder::setAuth( string $awsAccessKey, string $awsSecretKey );
```

Set AWS region:

```php
ElasticTranscoder::setRegion( string $region = 'us-east-1' );
```

Get HTTP status code of server response:

```php
ElasticTranscoder::getStatusCode();
```

Get server response:

```php
ElasticTranscoder::getResponse();
```

Get error message, if any:

```php
ElasticTranscoder::getErrorMsg();
```

<br />
<strong>More Information:</strong><br />
<a href="http://docs.aws.amazon.com/elastictranscoder/latest/developerguide/getting-started.html">Getting Started with Elastic Transcoder</a>

#### License ####

Released under the MIT license.

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/429c074cf07de7bee3ca6af902cd8141 "githalytics.com")](http://githalytics.com/LPology/ElasticTranscoderPHP)