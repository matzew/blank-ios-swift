node {
   stage('SCM') { 
     checkout scm
   }
   stage('CocoaPods') {
     sh "pod install"
   }
   stage('Build') {
      sh "xcodebuild -workspace blank-ios-app.xcworkspace -scheme blank-ios-app"
   }
}
