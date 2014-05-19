# http://lincolnmullen.com/blog/rake-and-pandoc/
require "rake/clean"

# Define inputs and outputs
MDFILES = FileList["*.md"]
PDFS = MDFILES.ext(".pdf")
DOCX = MDFILES.ext(".docx")
HTMLS = MDFILES.ext(".html")

OPTS = '-s'

# Clobber only PDFs and DOCXs we've generated
CLOBBER.include(HTMLS, PDFS, DOCX)

# Define bibliography and CSL files
BIB = "/Users/lmullen/acad/research/bib/master.bib"
CSL = "chicago-mullen.csl"

desc "Build all documents in all formats."
task :default => [:pdf, :docx, :html]

desc "Build HTMLs of all documents."
task :html => HTMLS
 
desc "Build PDFs of all documents."
task :pdf => PDFS

desc "Build DOCXs of all documents."
task :docx => DOCX

# Build HTMLs from Markdown source
rule ".html" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end

# Build PDFs from Markdown source
rule ".pdf" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end

# Build DOCXs from Markdown source
rule ".docx" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end