root = File.dirname(__FILE__)
src = File.join(root, 'typeset.scss')

desc "generate CSS from Sass source"
task :styles do
  dest = File.join(root, 'typeset.css')

  # Convert Scss source to CSS
  sh "sass --style expanded #{src} #{dest}"

  # Massage output
  css = IO.read(dest).gsub(%r{\*/\n/\*}, "*/\n\n/*").gsub(%r{(/\*\n  [A-Za-z.:; -]+\n\*/)}, "\\1\n")
  File.open(dest, "w") { |f| f.write(css) }
end

namespace :styles do
  desc "generate minified CSS from Sass source"
  task :minified do
    dest = File.join(root, 'typeset.min.css')
    sh "sass --style compressed #{src} #{dest}"
  end
end

# Make default task generate all CSS
task :default => ["styles", "styles:minified"]