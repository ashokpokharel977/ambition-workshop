**Hosting a Static Website in S3**
Open AWS Console, Type S3 on Search box or you can Search for S3 in All Services inside Storage.
Create a bucket  and give a unique name to your S3 bucket (name must not be repeated).
Click on create and your bucket is created.
Open your bucket and upload your static webpage from your local computer.
To Host  Static Webpage, we have to enable static website hosting. To do so, go to properties.  Click on static website hosting. Select **use this bucket to host a website**. On **index document**, type your landing webpage name. I will use index.html as my landing page and save it.
Click on index.html and open the Object URL of that page. This will not work because the uploaded object are not made public. So, it will give you access denied.
To make the object public, goto Permissions just next to Properties and edit it and uncheck  **Block** ***all*** **public access.**
Again open the Object URL of the index.html and see your working page. In some cases, it might be denied. In that case, click on the checkbox of index.html ,click on actions dropdown and make it public. Now it will work this time.
Final step is to make our bucket public. For this, go to Permissions again. You will see 4 options and click on Bucket policy.

```json
{
    "Version": "2012-10-17",
    "Id": "Policy1565606625345",
    "Statement": [
        {
            "Sid": "Stmt1565606605364",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::YOUR-BUCKET_NAME/*"
        }
    ]
}
```

Paste the above bucket policy and edit your bucket name in Resource section. 

## Create a sample static html file

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Cloud Workshop</title>
    <link href="https://fonts.googleapis.com/css?family=Roboto:700&display=swap" rel="stylesheet">
</head>
<style>
    body{
        margin: 0;
        padding: 0;
    }
    .hero{
        height: 100vh;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        background: #3494e6; /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #3494e6, #ec6ead); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #3494e6, #ec6ead); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    }
    .main-heading{
        text-align: center;
        font-family: 'Roboto', sans-serif;
        font-size: 5rem;
        font-weight: 700;
        color: white;
    }
</style>
<body>
    <div class="hero">
        <h1 class="main-heading">Cloud Fundamentals Workshop</h1>
    </div>
</body>
```

(**index.html**)

