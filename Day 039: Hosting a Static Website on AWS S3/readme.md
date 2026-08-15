
# Host a Static Website on AWS S3

## 🎯 Task Requirements

* Create an S3 bucket named `nautilus-web-13898`.
* Configure the bucket for static website hosting.
* Set `index.html` as the index document.
* Allow public access to the bucket.
* Upload the `index.html` file from `/root/` on the AWS client host.
* Verify that the website is accessible using the S3 website URL.

---

## Step 1: Open AWS S3

1. Log in to the **AWS Management Console**.
2. Search for **S3**.
3. Open the **S3** service.

---

## Step 2: Create the S3 Bucket

1. Click **Create bucket**.
2. Enter the bucket name:

```text
nautilus-web-13898
```

3. Select the required AWS Region.
4. Under **Block Public Access settings for this bucket**, uncheck:

```text
Block all public access
```

5. Check the acknowledgment box confirming that the bucket and its objects may become public.
6. Leave the remaining settings as default.
7. Click **Create bucket**.

---

## Step 3: Upload `index.html`

The file is available on the AWS client host at:

```text
/root/index.html
```

1. Open the bucket `nautilus-web-13898`.
2. Click **Upload**.
3. Click **Add files**.
4. Select the `index.html` file.
5. Click **Upload**.

After uploading, verify that the bucket contains:

```text
index.html
```

---

## Step 4: Enable Static Website Hosting

1. Open the S3 bucket.
2. Go to the **Properties** tab.
3. Scroll down to **Static website hosting**.
4. Click **Edit**.
5. Select **Enable**.
6. Choose:

```text
Host a static website
```

7. For **Index document**, enter:

```text
index.html
```

8. Click **Save changes**.

---

## Step 5: Configure Public Access

1. Go to the **Permissions** tab.
2. Scroll down to **Bucket policy**.
3. Click **Edit**.
4. Add the following policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::nautilus-web-13898/*"
        }
    ]
}
```

5. Click **Save changes**.

---

## Step 6: Verify the Website

1. Go to the **Properties** tab.
2. Scroll to **Static website hosting**.
3. Copy the **Bucket website endpoint**.
4. Open the endpoint in a browser.

The URL will look similar to:

```text
http://nautilus-web-13898.s3-website-<region>.amazonaws.com
```

If everything is configured correctly, the `index.html` webpage will be displayed.

---

## ✅ Verification Checklist

* [ ] S3 bucket `nautilus-web-13898` created.
* [ ] Block Public Access disabled.
* [ ] `index.html` uploaded successfully.
* [ ] Static website hosting enabled.
* [ ] Index document configured as `index.html`.
* [ ] Bucket policy allows public `s3:GetObject` access.
* [ ] Website is accessible through the S3 website endpoint.
