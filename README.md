rails_loggable
==============

Create Logs of changes of ActiveRecord in any model you need.

Log:

USER                           DESCRIPTION                                        DATE
admin ID: 1 - Model Debit Create State:                               2013-11-20 20:09:41 UTC
admin ID: 1 - Model Debit changed: State: canceled TO State: pending  2013-11-20 20:09:41 UTC
user  ID: 1 - Model Credit changed: State: canceled TO State: paid    2013-11-20 20:09:41 UTC

## Compatibility
Only Rails 4

* I will test with Rails 3

This is not similar proejct os PaperTrail and Auditable. It's only to create a register in Model LOG of changes 

## Installation 

1. Add `PaperTrail` to your `Gemfile`.

    `gem 'rails_loggable'`

2. You need to create Model LOG

    `class CreateLogs < ActiveRecord::Migration
      def change
        create_table :logs do |t|
          t.string :description
          t.references :user
          t.references :loggable, :polymorphic => true
          t.timestamps
        end
      end
    end`

3. Run the migration.

    `bundle exec rake db:migrate`

4. You need to put in you locale this:
    `en:
      rails_loggable:
        loggable_changed: "ID: %{id} - %{model} changed: %{before} TO %{after}"`

* recommend to create in your Rails APP/config/locale/en.railsloggable.yml

This project rocks and uses MIT-LICENSE.