fs     = require 'fs'
{exec} = require 'child_process'

appFiles  = [
  'src/header.coffee',
  'src/hamlruntime.coffee',
  'src/tokiniser.coffee',
  'src/buffer.coffee',
  'src/codegenerator.coffee',
  'src/jscodegenerator.coffee',
  'src/coffeecodegenerator.coffee',
  'src/filters.coffee',
  'src/haml.coffee'
]

specFiles = [
  'spec/haml-spec.coffee',
  'spec/filters-spec.coffee',
  'spec/interpolation-spec.coffee',
  'spec/haml-api-spec.coffee'
]

task 'build', 'Build haml.js', ->
  exec "coffee -c -j lib/haml.js #{appFiles.join(' ')} ", (err, stdout, stderr) ->
    throw err if err
    console.log stdout + stderr
  exec "coffee -c -j spec/haml-spec.js #{specFiles.join(' ')} ", (err, stdout, stderr) ->
    throw err if err
    console.log stdout + stderr
  exec "uglifyjs -o lib/haml.min.js lib/haml.js", (err, stdout, stderr) ->
    throw err if err
    console.log stdout + stderr
    