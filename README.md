# muquickstart
mu quickstart

# source
https://github.com/stelligent/mu/wiki/Quickstart

# steps

```
$ ls
index.html  README.md
$ mu init --port 80 --env
Writing config to '/home/yxiao/Documents/LEARNING/AWS/ECS_Fargate/mu/muquickstart/mu.yml'
Writing buildspec to '/home/yxiao/Documents/LEARNING/AWS/ECS_Fargate/mu/muquickstart/buildspec.yml'
Writing buildspec to '/home/yxiao/Documents/LEARNING/AWS/ECS_Fargate/mu/muquickstart/buildspec-test.yml'
Writing buildspec to '/home/yxiao/Documents/LEARNING/AWS/ECS_Fargate/mu/muquickstart/buildspec-prod.yml'

$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	buildspec-prod.yml
#	buildspec-test.yml
#	buildspec.yml
#	index.html
#	mu.yml
no changes added to commit (use "git add" and/or "git commit -a")
$ git info
git: 'info' is not a git command. See 'git --help'.

Did you mean one of these?
	init
	mailinfo
$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	buildspec-prod.yml
#	buildspec-test.yml
#	buildspec.yml
#	index.html
#	mu.yml
no changes added to commit (use "git add" and/or "git commit -a")
$ git add --all
$ git commit -m "mu init"
[master 09a6691] mu init
 Committer: Yanming Xiao <yxiao@secretgarden.home>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 6 files changed, 64 insertions(+)
 create mode 100644 buildspec-prod.yml
 create mode 100644 buildspec-test.yml
 create mode 100644 buildspec.yml
 create mode 100644 index.html
 create mode 100644 mu.yml
$ git push
warning: push.default is unset; its implicit value is changing in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the current behavior after the default changes, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

  git config --global push.default simple

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)

Username for 'https://github.com': yxiao168
Password for 'https://yxiao168@github.com': 
Counting objects: 8, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 860 bytes | 0 bytes/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/yxiao168/muquickstart.git
   5af7657..09a6691  master -> master
$ mu pipeline up
CodePipeline requires a personal access token from GitHub - https://github.com/settings/tokens
  GitHub token: : ****************************************

Upserting Bucket for CodeDeploy
Upserting Bucket for CodePipeline
  Created stack 'mu-bucket-codepipeline'
  Created stack 'mu-bucket-codedeploy'
-  mu-bucket-codepipeline:  mu-bucket-codepipeline (AWS::CloudFormation::Stack) CREATE_IN_PROGRESS User Initiated|  mu-bucket-codedeploy:  Bucket (AWS::S3::Bucket) CREATE_INUpserting IAM resources
  Created stack 'mu-iam-common'
  Created stack 'mu-iam-environment-acceptance'
  Created stack 'mu-iam-service-muquickstart-production'
  Created stack 'mu-iam-service-muquickstart-acceptance'
  Created stack 'mu-iam-environment-production'
  Created stack 'mu-iam-pipeline-muquickstart'
Upserting Pipeline for service 'muquickstart' ...
  Created stack 'mu-pipeline-muquickstart'
$ mu svc show

Pipeline URL:	https://console.aws.amazon.com/codesuite/codepipeline/pipelines/mu-muquickstart/view?region=us-east-1
+------------+----------+------------------------------------------+-------------+---------------------+
|   STAGE    |  ACTION  |                 REVISION                 |   STATUS    |     LAST UPDATE     |
+------------+----------+------------------------------------------+-------------+---------------------+
| Source     | Source   | 09a66915aade26ef55832e525551b656aae731e4 | Succeeded   | 2019-05-21 13:15:11 |
| Build      | Artifact |                                        - | Succeeded   | 2019-05-21 13:15:45 |
| Build      | Image    |                                        - | Succeeded   | 2019-05-21 13:16:18 |
| Acceptance | Deploy   |                                        - | InProgress  | 2019-05-21 13:16:19 |
| Acceptance | Test     |                                        - | -           |                   - |
| Production | Approve  |                                        - | -           |                   - |
| Production | Deploy   |                                        - | -           |                   - |
| Production | Test     |                                        - | -           |                   - |
+------------+----------+------------------------------------------+-------------+---------------------+

Deployments:
+-------------+----------+------------------+---------------------+
| ENVIRONMENT | REVISION |      STATUS      |     LAST UPDATE     |
+-------------+----------+------------------+---------------------+
| acceptance  | 09a6691  | CREATE_COMPLETE  | 2019-05-21 13:11:36 |
| production  | 09a6691  | CREATE_COMPLETE  | 2019-05-21 13:11:36 |
+-------------+----------+------------------+---------------------+

```
