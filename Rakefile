require 'rubygems'
require 'bundler'
require 'fileutils'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end

ROOT = File.dirname(__FILE__)

require 'rake'
require 'uglifier'

task :default do
  version = File.open(File.join(ROOT, 'VERSION')).read.strip
  output_path = File.join(ROOT, "dist")

  js_input_path = File.join('src', 'bootstrap-wysihtml.js')
  css_input_path = File.join('src', 'bootstrap-wysihtml.css')

  js_output_path = File.join(output_path, "bootstrap-wysihtml-#{version}.js")
  minified_js_output_path = File.join(output_path, "bootstrap-wysihtml-#{version}.min.js")
  css_output_path = File.join(output_path, "bootstrap-wysihtml-#{version}.css")

  minified_js = Uglifier.compile(File.read(js_input_path))
     
  File.open(minified_js_output_path, 'w') { |f| f.write(minified_js) } 
  File.open(js_output_path, 'w') { |f| f.write(File.read(js_input_path)) } 
  File.open(css_output_path, 'w') { |f| f.write(File.read(css_input_path)) }
end

