# Karma code coverage simple example
Related blog post can be found [here](http://codereform.com/blog/post/unit-test-code-with-jasmine-and-code-coverage-with-karma-coverage-using-istanbul/)

A Karma sample to setup code coverage with Istanbul.

Setup preprocessors, reporters coverage and reporters options.

karma.conf.js setup
```
module.exports = function (config) {
    config.set({
        basePath: '',
        frameworks: ['jasmine'],
        files: [
            'src/app/**/*.js',
            'src/spec/**/*.specs.js'
        ],
        preprocessors: {
            '**/src/app/*.js': ['coverage']
        },
        plugins: [
            'karma-jasmine',
            'karma-phantomjs-launcher',
            'karma-coverage'
        ],
        reporters: ['progress', 'coverage'],
        port: 9878,
        colors: true,
        logLevel: config.LOG_DEBUG,
        autowatch: true,
        browsers: ['PhantomJS'],
        singleRun: false,
        concurrency: Infinity,
        coverageReporter: {
            includeAllSources: true,
            dir: 'coverage/',
            reporters: [
                { type: "html", subdir: "html" },
                { type: 'text-summary' }
            ]
        }
    });
};
```

## Tests
A simple Calculator is tested from specs, working with `Jasmine` framework, in order to initiate the karma code coverage and its reports.

```
describe("Calculator Spec", function() {
    it("should add two and two and get four as a result", function() {
        // Arrange
        var calculator = new Calculator();

        // Act
        var result = calculator.add(2, 2);

        // Assert
        expect(result).toBe(4);
    });

    it("should subtract two and two and get zero as a result", function (){
        // Arrange
        var calculator = new Calculator();

        // Act
        var result = calculator.subtract(2, 2);

        // Assert
        expect(result).toBe(0);
    });
});
```
