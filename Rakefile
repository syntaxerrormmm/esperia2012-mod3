#vim: set fontencoding=utf-8
require 'rake/clean'

MAIN = 'modulo3.pdf'

CLEAN.add(FileList['*.aux'])
CLEAN.add(FileList['*.log'])
CLEAN.add(FileList['*.toc'])
CLEAN.add(FileList['*.nav'])
CLEAN.add(FileList['*.out'])
CLEAN.add(FileList['*.snm'])
CLOBBER.add(MAIN)

task :default => MAIN

rule '.pdf' => '.tex' do |t|
  basename = File.basename(t.source, '.tex')
  if not File.exist?(basename + '.aux')
    sh %[xelatex #{basename}]
  end
  sh %[xelatex #{basename}]
end

task :upload => MAIN do
  sh %[scp modulo3.pdf r2d2:/srv/http/bglug/slides/modulo3.pdf]
end
