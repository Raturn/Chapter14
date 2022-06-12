# 비디오 재생 앱
AVPlayerViewController를 이용하여 내부 저장 동영상과 외부의 링크된 비디오 파일을 재생하는 앱입니다.

<img src="https://user-images.githubusercontent.com/105588287/173236284-6651ff36-ce80-499b-a016-d2b00961382e.png" width="250" height="600"/> <img src="https://user-images.githubusercontent.com/105588287/173236286-16d10057-9fe7-4ed5-bfc5-16998103f996.png" width="250" height="600"/> <img src="https://user-images.githubusercontent.com/105588287/173236287-89619a25-5225-4fc4-945b-11e3c9e08263.png" width="250" height="600"/>

# 환경
Xcord

# Source
**내부 동영상**\
비디오가 저장된 파일 경로를 받아오며 내부의 파일명을 NSURL 형식으로 변경

    @IBAction func btnPlayInterNalMovie(_ sender: UIButton) {
        let filePath:String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4")
        
        let url = NSURL(fileURLWithPath: filePath!)
        
        playVideo(url: url)
    }
    
**외부 동영상**\
외부의 링크된 비디오 파일 주소를 NSURL 형식으로 변경하며 AVPlayerViewController의 인스턴스를 설정합니다.


    @IBAction func btnPlayExternalMovie(_ sender: UIButton) {
        let url = NSURL(string: "https://dl.dropboxusercontent.com/s/e38auz050w2mvud/Fireworks.mp4")!
        
        playVideo(url: url)
    }
    
    private func playVideo(url: NSURL) {
        let playerController = AVPlayerViewController()
        
        let player = AVPlayer(url: url as URL)
        
        playerController.player = player
        
        self.present(playerController, animated: true) {
            player.play()
        }
    }
    
}
