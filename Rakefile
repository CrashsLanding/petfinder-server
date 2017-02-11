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
    default_photo_id = ENV['PETFINDER_DEFAULT_PHOTO_ID']
    default_photo_url = ENV['PETFINDER_DEFAULT_PHOTO_URL']

    PetFinderCreateDatabase.new(database_url).create_db
  end

  task import: :dotenv do
    database_url = ENV['DATABASE_URL']
    api_key = ENV['PETFINDER_API_KEY']
    api_secret = ENV['PETFINDER_API_SECRET']
    shelter_ids = ENV['PETFINDER_SHELTER_IDS']
    default_photo_id = ENV['PETFINDER_DEFAULT_PHOTO_ID']
    default_photo_url = ENV['PETFINDER_DEFAULT_PHOTO_URL']

    PetfinderScheduler.new(database_url, api_key, api_secret, shelter_ids, default_photo_id, default_photo_url).fill_db()
  end

  task update: :dotenv do
    database_url = ENV['DATABASE_URL']
    api_key = ENV['PETFINDER_API_KEY']
    api_secret = ENV['PETFINDER_API_SECRET']
    shelter_ids = ENV['PETFINDER_SHELTER_IDS']
    default_photo_id = ENV['PETFINDER_DEFAULT_PHOTO_ID']
    default_photo_url = ENV['PETFINDER_DEFAULT_PHOTO_URL']

    db_exists = PetFinderCreateDatabase.new(database_url).db_exists?
    PetFinderCreateDatabase.new(database_url).create_db unless db_exists

    PetfinderScheduler.new(database_url, api_key, api_secret, shelter_ids, default_photo_id, default_photo_url).fill_db()
  end
end
