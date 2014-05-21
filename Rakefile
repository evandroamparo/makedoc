# http://lincolnmullen.com/blog/rake-and-pandoc/
require "rake/clean"

# Define inputs and outputs
src = directory "src"
build = directory "build"
MDFILES = FileList["#{src}/*.md"]
PDF = " #{build}/Doc.pdf"
INDEX = " #{build}/index.html"
HTMLS = MDFILES.ext(".html")

OPTS = "-s"

CLEAN.include(FileList["tex2pdf**"])
CLOBBER.include(build.to_s)

desc "Build all documents in all formats."
task :default => [src, :index, :htmls, :pdf]

desc "Build HTMLs of all documents."
task :htmls => build
task :htmls => HTMLS
 
desc "Build one PDF of all documents."
task :pdf => build do |t|
  sh "pandoc --latex-engine=xelatex #{OPTS} #{MDFILES} -o #{PDF}"
end

desc "Build one HTML of all documents."
task :index => build do |t|
  sh "pandoc #{OPTS} #{MDFILES} -o #{INDEX}"
end

# Build HTMLs from Markdown source
rule ".html" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{build}/#{File.basename(t.name)}"
end