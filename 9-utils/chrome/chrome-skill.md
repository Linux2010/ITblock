# chrome-skills

- skill
  - [chrome安装配置禁止升级](https://chenyufeng.blog.csdn.net/article/details/78568919?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-78568919-blog-124563235.pc_relevant_3mothn_strategy_recovery&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-78568919-blog-124563235.pc_relevant_3mothn_strategy_recovery&utm_relevant_index=1)
    - 方法1：
      - cd ~/Library/Google
      - sudo chown root:wheel GoogleSoftwareUpdate
    - 方法2：
      - cd /Library/Google/GoogleSoftwareUpdate
      - 删除 GoogleSoftwareUpdate.bundle