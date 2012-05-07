desc "generate CSS from Sass source"
task :styles do
  root = File.dirname(__FILE__)
  src = File.join(root, 'src', 'typeset.scss')
  dest = File.join(root, 'typeset.css')
  sh "sass --style expanded #{src} #{dest}"
  IO.write(dest,
    IO.read(dest)
      .gsub(%r{\*/\n/\*}, "*/\n\n/*")
      .gsub(%r{(/\*\n  [A-Za-z.:; -]+\n\*/)}, "\\1\n")
  )
end

task :default => :styles
