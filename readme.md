
Set up AWS commandline tools
http://docs.aws.amazon.com/cli/latest/userguide/installing.html

Set up AWS credentials
http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

ls -l $HOME/.aws
total 16
-rw-------  1 brianom  staff   29  2 Jun  2015 config
-rw-------  1 brianom  staff  116  2 Jun  2015 credentials


> aws s3api create-bucket --bucket seed-site

{
    "Location": "/seed-site"
}

> aws s3api create-bucket --bucket test

An error occurred (BucketAlreadyExists) when calling the CreateBucket operation: The requested bucket name is not available. The bucket namespace is shared by all users of the system. Please select a different name and try again.

> aws s3 cp index.html s3://seed-site/
upload: ./index.html to s3://seed-site/index.html

> aws s3 cp . s3://seed-site/ --recursive --exclude "*" --include "*.jpg" --include "*.html" --acl public-read

> aws s3 ls s3://seed-site/
2017-06-07 06:38:29     329903 dead-seed.jpg
2017-06-07 06:38:29       1608 error.html
2017-06-07 06:38:29       1587 index.html
2017-06-07 06:38:29     201254 seed.jpg



> aws s3 website s3://seed-site/ --index-document index.html --error-document error.html

Ta-Da
https://s3.amazonaws.com/seed-site/
