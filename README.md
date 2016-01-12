# Technekes Best Practices
## Rake
### Logging

add a logger task to `utils.rake`

```ruby
task :logger => :environment do
  logger           = Logger.new(STDOUT)
  logger.formatter = Logger::Formatter.new
  logger.level     = Logger::INFO
  Rails.logger     = logger
end
```

depend on `logger` task instead of `environment` & use Rails.logger (NEVER puts!!!)

```ruby
task :some_task => :logger do
  Rails.logger.info "Some task here"
end

# Output: I, [2016-01-12T22:09:15.591225 #27687]  INFO -- : Some task here
```

enjoy better logs!
