# aws-eu-data-sovereignty-issues
PoC &amp; use cases in which a EU customer is forced to transfer data (or crypto material) outside of EU when using AWS services. I aim to document the less-obvious ones, where you first think that a given service is okay because its compute runs in EU, but in fact some datas or crypto material gets us-based.

## ACM + Cloudfront

Use case description: you want to use AWS's CDN, AWS CloudFront, with your own domain name to expose a service using https.

_To use an ACM certificate with Amazon CloudFront, you must request or import the certificate in the US East (N. Virginia) region. ACM certificates in this region that are associated with a CloudFront distribution are distributed to all the geographic locations configured for that distribution._

Reference: [AWS Certificate Manager - Supported Regions](https://docs.aws.amazon.com/acm/latest/userguide/acm-regions.html)


## AWS Cognito user pools with a custom domain

Use case description: AWS Cognito user pools can use, and expose to users, an FQDN in the format of `CUSTOMIZABLESTRING.auth.eu-west-1.amazoncognito.com`.

If you want to customize this this domain name, AWS instructs you to create your ACM Certificate in us-east-1.

Reference: [Amazon Cognito - Using your own domain for the hosted UI](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-add-custom-domain.html)