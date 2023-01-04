A　put_policy.py

```
trufflehog https://haugfactory.com/orcadmin/aws_scripts
```

~~~~~~~~~~~~~~~~~~~~~
Reason: High Entropy
Date: 2022-09-07 23:53:32
Hash: 3476397f95da11a776d4118f1f9ae6c9d4afd0c9
Filepath: put_policy.py
Branch: origin/main
Commit: added

@@ -4,8 +4,8 @@ import json
 
 iam = boto3.client('iam',
     region_name='us-east-1',
-    aws_access_key_id=ACCESSKEYID,
-    aws_secret_access_key=SECRETACCESSKEY,
+    aws_access_key_id="AKIAAIDAYRANYAHGQOHD",
+    aws_secret_access_key="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",
 )
 # arn:aws:ec2:us-east-1:accountid:instance/*
 response = iam.put_user_policy(

~~~~~~~~~~~~~~~~~~~~~
