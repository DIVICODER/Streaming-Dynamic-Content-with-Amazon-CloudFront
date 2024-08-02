
https://github.com/user-attachments/assets/00e12c67-96dd-4d0f-bb42-a78c9c385ade
# Streaming-Dynamic-Content-with-Amazon-CloudFront
This repository provides a step-by-step guide to create a scalable and efficient video streaming service. By leveraging AWS services, we can transcode video files into multiple resolutions and deliver them dynamically based on the user's internet connection.

## Create S3 bucket:
search for `s3` in the search bar.
then click `bucket` on the left side.
create a bucket with a name.
`upload a video` into the s3 created bucket.

## Create Amazon CloudFront Distribution:
search for `cloudfront` in console.
click create `cloudfront distribution`.
give the bucket name in the origin domain.
enable origin shield `no`.(to make public)
WAF (do not enable security).
`Create distribution`.

## Create Amazon Elastic Transcoder Pipeline:
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

## Create Job:





https://github.com/user-attachments/assets/106203d6-764c-4fd6-af97-e4ec64a004c5


  


