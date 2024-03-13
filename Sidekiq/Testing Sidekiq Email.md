# Sidekiq
## Testing email sent
launch sidekiq en localhost 
```shell
bundle exec sidekiq --environment development -C config/sidekiq.yml
```

Create an enrollment in localhost
validate the form 

Sidekiq logs will show in console.

### Clear Sidekiq queues in console
```ruby
#require 'sidekiq/api'
Sidekiq::Queue.all.each(&:clear)
Sidekiq::RetrySet.new.clear
Sidekiq::ScheduledSet.new.clear
Sidekiq::DeadSet.new.clear
```


### How to Test a worker process
**Instruction to test the worker cron job**

-   in a console window, open the rails console
```ruby
bundle exec rails c
```

-   Clear all Sidekiq Queues
```ruby
Sidekiq::Queue.all.each(&:clear)
Sidekiq::RetrySet.new.clear
Sidekiq::ScheduledSet.new.clear
Sidekiq::DeadSet.new.clear
```

-   Launch Sidekiq :
```ruby
bundle exec sidekiq --environment development -C config/sidekiq.yml
```

[![Capture d’écran 2023-02-03 à 14 26 37](https://user-images.githubusercontent.com/43042737/216614780-8f35eebe-66ab-4216-bf10-eb86830704cd.png)](https://user-images.githubusercontent.com/43042737/216614780-8f35eebe-66ab-4216-bf10-eb86830704cd.png)

The following lines about the cron schedule expression with worker and sidekiq queue should be displayed :
```shell
2023-02-03T13:25:18.780Z pid=24953 tid=7rl INFO: Scheduling schedule_reminder_email_for_draft_enrollments_worker {"cron"=>"0 6 * * *", "class"=>"ScheduleReminderEmailForDraftEnrollmentsWorker", "queue"=>"reminders"}
2023-02-03T13:25:18.782Z pid=24953 tid=7rl INFO: Scheduling schedule_reminder_email_for_change_requested_enrollments_worker {"cron"=>"0 7 * * *", "class"=>"ScheduleReminderEmailForChangeRequestedEnrollmentsWorker", "queue"=>"reminders"}
```

-   Launch the project in localhost (frontend and backend)
-   Launch a rails console in a new console window and call the Worker
```ruby
bundle exec rails c
load "schedule_reminder_email_for_draft_enrollments_worker.rb"
# => true
ScheduleReminderEmailForDraftEnrollmentsWorker.new.perform
```


### Links
[Sending emails with ActionMailer and Sidekiq](https://gist.github.com/maxivak/690e6c353f65a86a4af9)

https://josh.works/sidekiq-in-practice-notes

