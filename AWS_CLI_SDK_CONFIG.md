* AWS
    * have an AWS account
    * Create an IAM user here
		https://console.aws.amazon.com/iam/
        * Users > Add user
            * Set name, access type is programmatic
        * Add user to group
            * Create or choose existing group with S3 Full access(can tailor this if you want)
            * Tags (skip)
            * Create user
            * Be sure on the next page (success) to get the access key id and secret access key, one of these is only shown once otherwise have to regenerate it, you’ll need this for AWS cli
            * Access key id: ###
            * Secret access key: ###
    * Next look up how to install AWS CLI for your OS eg. MacOS/Windows/Linux
        * Verify the installation worked
            * Should be able to do something like: $aws —version and get some output about was-cli
            * Then run $aws configure to generate your .aws folder which will have your credentials file
            * Then you need to find your credentials file
                * Here you’ll be prompted to enter your AWS Access Key ID and AWS Secret Access Key from the IAM step
                * For the next two fields (region name/output format) you can keep them as none
                * Your ~/aws/credentials path will vary per OS but generally it’s at the “home” folder