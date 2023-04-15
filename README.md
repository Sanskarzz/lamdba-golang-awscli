# lamdba-golang-awscli
# Commands


aws iam create-role --role-name lambda-exm --assume-role-policy-document '{"Version": "2012-10-17","Statement": [{ "Effect": "Allow", "Principal": {"Service": "lambda.amazonaws.com"}, "Action": "sts:AssumeRole"}]}'




aws iam create-role --role-name lambda-ex --assume-role-policy-document file://trust-policy.json


aws iam attach-role-policy --role-name lambda-ex --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole


go get github.com/aws/aws-lambda-go

go mod tidy

go build main.go

sudo zip function.zip main.go

 aws lambda create-function --function-name go-lambda-exm \
> --zip-file fileb://function.zip --handler main --runtime go1.x \
> --role arn:aws:iam::456457959053:role/lambda-ex

aws lambda invoke --function-name go-lambda-exm --cli-binary-format raw-in-base64-out --payload `{"What is your name ?": "Jim","How old are you?": 33}` output.txt
