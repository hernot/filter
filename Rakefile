require 'fileutils'
require 'rake/clean'

def make_tds(name, files, doc)
  tex_dir = "#{name}/tex/context/third/#{name}"
  doc_dir = "#{name}/doc/context/third/#{name}"
  sh "mkdir -p #{tex_dir}"
  sh "mkdir -p #{doc_dir}"
  files.each do |tex|
    FileUtils.cp tex, tex_dir
  end
  FileUtils.cp doc, (doc_dir + "/#{name}.txt")
end

FILTER_TEX = %W[t-filter.mkii t-filter.mkiv t-module-catcodes.tex]
FILTER_DOC = "README.md"

VIM_TEX = %W[t-vim.tex t-syntax-groups.tex t-syntax-highlight.mkii t-syntax-highlight.mkiv]
VIM_DOC = "vim-README.md"

task :clean_vim do
  sh "rm -rf vim"
end

task :clean_filter do
  sh "rm -rf filter"
end

desc "Make TDS for filter module"
task :filter => :clean_filter do
  make_tds :filter, FILTER_TEX, FILTER_DOC
  sh "zip -r filter.zip filter"
end

desc "Make TDS for vim module"
task :vim => :clean_vim do
  make_tds :vim, VIM_TEX, VIM_DOC
  sh "zip -r vim.zip vim"
end

CLEAN.include('*.zip')


