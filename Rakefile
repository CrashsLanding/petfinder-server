require_relative 'petfinder_scheduler'
require_relative 'petfindercreatedatabase'
require 'dotenv/tasks'

namespace :db do
  desc 'Reprovision the database'
  task create: :dotenv do
    database_url = ENV['DATABASE_URL']
    api_key = ENV['PETFINDER_API_KEY']
    api_secret = ENV['PETFINDER_API_SECRET']
    shelter_ids = ENV['PETFINDER_SHELTER_IDS']

    PetFinderCreateDatabase.new(database_url).create_db
  end

  task import: :dotenv do
    database_url = ENV['DATABASE_URL']
    api_key = ENV['PETFINDER_API_KEY']
    api_secret = ENV['PETFINDER_API_SECRET']
    shelter_ids = ENV['PETFINDER_SHELTER_IDS']

    PetfinderScheduler.new(database_url, api_key, api_secret, shelter_ids).fill_db()
  end
end
