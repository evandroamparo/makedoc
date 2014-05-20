# http://lincolnmullen.com/blog/rake-and-pandoc/
require "rake/clean"

# Define inputs and outputs
IN_DIR = "src"
MDFILES = FileList["#{IN_DIR}/*.md"]
PDF = "doc.pdf"
HTMLS = MDFILES.ext(".html")

OPTS = "-s"

CLEAN.include(FileList["tex2pdf**"])
CLOBBER.include(HTMLS, PDF)

desc "Build all documents in all formats."
task :default => [IN_DIR, :pdf, :html]

directory "temp"

desc "Build HTMLs of all documents."
task :html => HTMLS
 
desc "Build PDFs of all documents."
task :pdf do |t|
  sh "pandoc --latex-engine=xelatex #{OPTS} #{MDFILES} -o doc.pdf"
end

# Build HTMLs from Markdown source
rule ".html" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end