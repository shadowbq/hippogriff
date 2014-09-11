require 'bundler'
#Bundler::GemHelper.install_tasks

@compressed_lib = "./vendor/compressed"

task :default => :test

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'tests'
  test.test_files = Dir[ "test/test_*.rb"]
  test.verbose = true
end

namespace :geoip do
  desc "Update GeoIP City data file"
  task :update_city_lite => :vendor do
    %x[wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz && mv GeoLiteCity.dat.gz #{@compressed_lib}]
  end

  desc "Update GeoIP Country data file"
  task :update_country_lite => :vendor do
    %x[wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz && mv GeoIP.dat.gz #{@compressed_lib}]
  end

  desc "Update GeoIP to ASN data file"
  task :update_asn => :vendor do
    %x[wget http://geolite.maxmind.com/download/geoip/database/asnum/GeoIPASNum.dat.gz && mv GeoIP.dat.gz #{@compressed_lib}]
  end

  task :vendor do
    %x{mkdir -p vendor}
  end
end
