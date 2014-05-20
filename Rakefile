# http://lincolnmullen.com/blog/rake-and-pandoc/
require "rake/clean"

# Define inputs and outputs
IN_DIR = "src"
MDFILES = FileList["#{IN_DIR}/*.md"]
PDF = "Doc.pdf"
INDEX = "index.html"
HTMLS = MDFILES.ext(".html")

OPTS = "-s --chapters"

CLEAN.include(FileList["tex2pdf**"])
CLOBBER.include(INDEX, HTMLS, PDF)

desc "Build all documents in all formats."
task :default => [IN_DIR, :index, :htmls, :pdf]

desc "Build HTMLs of all documents."
task :htmls => HTMLS
 
desc "Build one PDF of all documents."
task :pdf do |t|
  sh "pandoc --latex-engine=xelatex #{OPTS} #{MDFILES} -o #{PDF}"
end

desc "Build one HTML of all documents."
task :index do |t|
  sh "pandoc #{OPTS} #{MDFILES} -o #{INDEX}"
end

# Build HTMLs from Markdown source
rule ".html" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end