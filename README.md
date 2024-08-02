
# Streaming-Dynamic-Content-with-Amazon-CloudFront

This repository provides a step-by-step guide to create a scalable and efficient video streaming service. By leveraging AWS services, we can transcode video files into multiple resolutions and deliver them dynamically based on the user's internet connection.

### IF WE DONT USE AET(AMAZON ELASTIC TRANSCODER)
![Screenshot (5)](https://github.com/user-attachments/assets/43b2d96e-60c3-4984-bb83-9b28261cfce7)

### IF WE USE AET
![Screenshot (3)](https://github.com/user-attachments/assets/0ecf1fba-aa41-42f7-9758-976b0430db96)

## Create S3 bucket:
search for `s3` in the search bar.
then click `bucket` on the left side.
create a bucket with a name.
`upload a video` into the s3 created bucket.

## Create Amazon CloudFront Distribution:
-------------
search for `cloudfront` in console.
click create `cloudfront distribution`.
give the bucket name in the origin domain.
enable origin shield `no`.(to make public)
WAF (do not enable security).
`Create distribution`.

## Create Amazon Elastic Transcoder Pipeline:
--------------
search for `elastic transcoder` in search bar.
on left side click `pipeline`.
give name for the pipeline( example- inputpipeline).
provide IAM Role -> `amazonelastictranscoderole`. (to let the AET to S3 bucket).
configuration  S3 bucket ->
  bucket choose the bucket.
  storage class `standard`.
tumbnails bucket ( to store tumbnail also in the same bucket).
  storage class choose `reduceredundancy`.
`Create Pipeline`.

## Create Job: (AET work only via pipeline- transcode inputfile->multibit)
-------------------
in AET click `create new job`.
choose pipeline name (inputpipeline).
in output key- `output/` (it means within output folder it will be placing the output).
in input key- `choose s3foldername/videoname.mp4.

## Configuring Output Details: (configure the multibits like creating 3 files in output folder for 2mbps,1.5mbps and 1mbps so on)
------------------
in preset, choose `system preset HLS 2M`.
segment duration `choose the time in which the original video should be slitted like for each 10 sec theymake video`.
in output key[HLS20M] name segments.
add another output HLS1.5M, HLS1M as the prefix.

## Configure a Playlist:
------------------
the playlist will contains multiple individual bit rate. with the help of playlist single url for device. using which we will run the video streaming.
choose `add playlist` give name for playlist,format as `HLSv3` and also dont forget to select the 3 quality that you have created (HLS1M,HLS1.5M,HLS2M...).
`Create new job`.

## Testing Playlist:
-----------------
go to cloudfront-> choose amazon cloudfront-> change the inprogress to enabled.

### now to run this use the bellow format
`http://<CloudFront domain name>/<playlist file path in Amazon S3 bucket>`



https://github.com/user-attachments/assets/106203d6-764c-4fd6-af97-e4ec64a004c5


  


