# GitLabRunnerCICD

GitLab CI/CDを試せるリポジトリです。

GitLabのリポジトリにミラーしてCI/CDを動かしています。    

[kichiemon/GitLabRunnerCICD](https://gitlab.com/kichiemon/GitLabRunnerCICD)

## Required

- Xcode10.2.1

## iOSのリポジトリにGitLabRunnerを導入する手順

1. Macにgitlab-runner をインストール
```.bash
# see -  https://docs.gitlab.com/runner/install/osx.html#manual-installation-official
$ gitlab-runner install
```

2. GitLabに登録する。coordinator URL, token, description, tag, executorを回答する
こちらを参考に。https://docs.gitlab.com/runner/register/#macos
```.bash
$ gitlab-runner register
Runtime platform                                    arch=amd64 os=darwin pid=38071 revision=d0b76032 version=12.0.2
WARNING: Running in user-mode.
WARNING: Use sudo for system-mode:
WARNING: $ sudo gitlab-runner...

Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
https://gitlab.com/
Please enter the gitlab-ci token for this runner:
xxxxxxxxxxxxxxxxxxxxxxxxxxx
Please enter the gitlab-ci description for this runner:
[yyyyyyyyyy]: gitalb-ios-project
Please enter the gitlab-ci tags for this runner (comma separated):
ios
Registering runner... succeeded                     runner=n8WEcMNf
Please enter the executor: ssh, kubernetes, docker, docker-ssh, virtualbox, docker+machine, docker-ssh+machine, parallels, shell:
shell
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```

3. gitlab-runnerの登録が正しくできているか確認する
```.bash
$ gitlab-runner verify
```

4. あとは新しくブランチを作ったり、PUSHすれば、GitLabRunnerが動き始めるはずです


## GitLab Runnerの操作

* gitlab-runnerのコマンド確認
```.bash
$ gitlab-runner -h
```

* gitlab-runnerを停止
```.bash
$ gitlab-runner stop
```

* gitlab-runnerを起動
```.bash
$ gitlab-runner start
```

* gitlab-runnerをデバッグモードで走らせる
```.bash
$ gitlab-runner --debug run
```

* gitlab-runnerの登録を解除する
```.bash
$ gitlab-runner unregister
```

* gitlab-runnerでCIジョブを実行する
```.bash
gitlab-runner exec shell build
```


