# http://lincolnmullen.com/blog/rake-and-pandoc/
require "rake/clean"

# Define inputs and outputs
MDFILES = FileList["*.md"]
PDFS = MDFILES.ext(".pdf")
DOCX = MDFILES.ext(".docx")
HTMLS = MDFILES.ext(".html")

OPTS = '-s'
OUT_DIR = "output"
PDF_OUT = "#{OUT_DIR}/pdf"

# Clobber only PDFs and DOCXs we've generated
CLOBBER.include(HTMLS, PDFS, DOCX, OUT_DIR)

# Define bibliography and CSL files
BIB = "/Users/lmullen/acad/research/bib/master.bib"
CSL = "chicago-mullen.csl"

directory PDF_OUT

desc "Build all documents in all formats."
task :default => [:pdf, :docx, :html]

desc "Build HTMLs of all documents."
task :html => HTMLS
 
desc "Build PDFs of all documents."
task :pdf => PDF_OUT do |t|
  sh "pandoc #{OPTS} #{MDFILES} -o #{OUT_DIR}/pdf/doc.pdf"
end

desc "Build DOCXs of all documents."
task :docx => DOCX

# Build HTMLs from Markdown source
rule ".html" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end

# Build DOCXs from Markdown source
rule ".docx" => ".md" do |t|
  sh "pandoc #{OPTS} #{t.source} -o #{t.name}"
end