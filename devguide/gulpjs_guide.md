# Gulp.js 가이드

UCARE 공통 js 의 압축 및 난독화를 위한 내용을 설명합니다.

### Gulp.js 참조 URL
  - [gulp 시작하기](https://valuefactory.tistory.com/314)
  - [gulp 로 js파일 Minify 및 Merge 하기](https://okayoon.tistory.com/entry/gulp%EB%A1%9C-js-%ED%8C%8C%EC%9D%BC-css%ED%8C%8C%EC%9D%BC-Minify-%EB%B0%8F-Merge%ED%95%98%EA%B8%B0)



### Gulp.js 시작하기
1. Gulp install
    ```
    npm install --global gulp-cli
    npm install --save-dev gulp    
    ```
    Gulp install이 성공적으로 완료되었다면 버전 정보를 확인할 수 있습니다.
    ```
    gulp -v
    ```

2. module install   
    minify와 merge를 진행하기 위해 각각의 module을 install한다.
    ```
    npm install --save-dev gulp-concat
    npm install --save-dev gulp-uglify
    ```

3. gulp 실행 파일 생성   
    root에 gulpfile.js 파일을 생성한다.
    ```js
    const gulp = require('gulp');
    const concat = require('gulp-concat'); 
    const uglify = require('gulp-uglify');

    // 자바스크립트 파일을 병합
    gulp.task('concat', function() {
        return gulp.src([
                // 우선적으로 병합 수행할 파일
                './static/js/ucare/uclib_module.js',
                // 수행 파일
                './static/js/ucare/*.js',
                // 제외 파일
                // '!./static/js/ucare/uclib_default.js',
                '!./static/js/ucare/uclib_editor_namo.js',
                '!./static/js/ucare/uclib_highcharts.js',
                '!./static/js/ucare/uclib_password.js'
            ])
            .pipe(uglify()) // 난독화
            .pipe(concat('ucare.min.js')) // ucare.min.js로 파일이름을 짓고 병합
            .pipe(gulp.dest('./static/js/ucare/dist')); // dist 폴더에 병합한 파일 생성
    });

    // watch 설정
    //  : 해당 경로의 파일이 변경되면 concat을 실행한다.
    gulp.task('watch', function(){ 
        gulp.watch('./static/js/ucare/*.js', gulp.series('concat'));
    });

    // watch 설정하지 않을 경우 parameter에서 watch 제외
    gulp.task('default', gulp.series('concat'), 'watch');
    ```

4. gulp 실행
    ```
    gulp
    ```

### 실행 결과
- 생성된 dist 폴더   
<img src="https://user-images.githubusercontent.com/52988840/116836612-21170180-ac02-11eb-9173-bfeb20922894.png">


- 압축 및 난독화된 ucare.min.js 파일   
<img src="https://user-images.githubusercontent.com/52988840/116836615-24aa8880-ac02-11eb-8d4c-9882a50bdea6.png">

- ucare.min.js 적용   
<img src="https://user-images.githubusercontent.com/52988840/116836881-42c4b880-ac03-11eb-9c46-27ba7c78360d.png" style="width:100%">
