<template>
  <v-app>
    <v-main>
      <v-card class="ma-5" elevation="5" shaped>
        <v-card-text>
          <v-container fluid>
            <v-row class="align-center">
              <v-col class="d-flex-column">
                <div class="text-h3 text-uppercase blue--text font-weight-bold">{{ name }}</div>
                <div class="text-h5">{{ position }}</div>
              </v-col>
              <v-col class="d-flex">
                <v-spacer></v-spacer>
                <v-avatar size="100">
                  <v-img src="profile.jpg"></v-img>
                </v-avatar>
              </v-col>
              <v-col style="border-left: 1px solid rgba(0, 0, 0, 0.08);">
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-cellphone</v-icon>
                  <v-btn text :href="`tel:${tel}`">{{ tel }}</v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-email</v-icon>
                  <v-btn text class="text-none" :href="`mailto:${email}`">
                    {{
                    email
                    }}
                  </v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-linkedin</v-icon>
                  <v-btn text :href="linkedin">www.linkedin.com</v-btn>
                </div>
                <div class="d-flex align-center">
                  <v-icon class="mr-3">mdi-github</v-icon>
                  <v-btn text :href="github">github.com</v-btn>
                </div>
              </v-col>
            </v-row>
            <v-row class="my-5" style="border-top: 1px solid rgba(0, 0, 0, 0.08);">
              <v-col></v-col>
            </v-row>
            <v-row>
              <v-hover v-slot:default="{ hover }">
                <v-card outline :elevation="hover ? 2 : 0" width="100%" class="ma-3">
                  <v-card-title>WORK EXPERIENCE</v-card-title>
                  <v-card-text>
                    <v-timeline dense>
                      <v-timeline-item v-for="(experience, i) of workExperience" :key="i">
                        <template v-slot:icon>
                          <v-avatar tile>
                            <v-img :src="experience.logo"></v-img>
                          </v-avatar>
                        </template>
                        <v-divider></v-divider>
                        <div>
                          {{ experience.when }}&nbsp;|&nbsp;{{
                          experience.where
                          }}
                        </div>
                        <div>{{ experience.position }}</div>
                        <div>{{ experience.role }}</div>
                      </v-timeline-item>
                    </v-timeline>
                  </v-card-text>
                </v-card>
              </v-hover>
              <v-hover v-for="(title, i) of titles" :key="i" v-slot:default="{ hover }">
                <v-card outline :elevation="hover ? 2 : 0" width="100%" class="ma-3">
                  <v-card-title>{{title}}</v-card-title>
                  <v-card-text>
                    <v-expansion-panels accordion multiple flat hover>
                      <v-expansion-panel
                        v-for="(item, i) in self[title.toLowerCase()]"
                        :key="i"
                        :readonly="!(item.contents.length || item.img.length)"
                      >
                        <v-expansion-panel-header>
                          <div class="d-flex justify-space-between">
                            <span>{{ item.title }}</span>
                            <span>{{ item.date }}</span>
                          </div>
                        </v-expansion-panel-header>
                        <v-expansion-panel-content>
                          <template v-if="item.contents && item.contents.length">
                            <div v-for="(content, i) of item.contents" :key="i">{{ content }}</div>
                          </template>
                          <template v-if="item.img && item.contents.length">
                            <v-img v-for="(img, i) of item.img" :key="i" :src="img"></v-img>
                          </template>
                        </v-expansion-panel-content>
                      </v-expansion-panel>
                    </v-expansion-panels>
                  </v-card-text>
                </v-card>
              </v-hover>
            </v-row>
            <v-row></v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-main>

    <v-footer app elevation="1">
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().toLocaleDateString() }}</div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  head() {
    return {
      title: '[Resume] Kyongsik Choi',
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' },
        { name: 'author', content: 'Kyongsik Choi' },
        { name: 'title', content: '[Resume] Kyongsik Choi' },
        {
          name: 'description',
          content:
            'WORK EXPERIENCE, PROJECTS, INFORMATION, EDUCATION, AWARDS Information',
        },
        { property: 'og:type', content: 'website' },
        { property: 'og:url', content: 'https://kschoi.netlify.app/' },
        { property: 'og:title', content: '[Resume] Kyongsik Choi' },
        {
          property: 'og:description',
          content:
            'WORK EXPERIENCE, PROJECTS, INFORMATION, EDUCATION, AWARDS Information',
        },
        {
          property: 'og:image',
          content: 'https://kschoi.netlify.app/profile.jpg',
        },
        { property: 'twitter:card', content: 'summary_large_image' },
        { property: 'twitter:url', content: 'https://kschoi.netlify.app/' },
        { property: 'twitter:title', content: '[Resume] Kyongsik Choi' },
        {
          property: 'twitter:description',
          content:
            'WORK EXPERIENCE, PROJECTS, INFORMATION, EDUCATION, AWARDS Information',
        },
        {
          property: 'twitter:image',
          content: 'https://kschoi.netlify.app/profile.jpg',
        },
      ],
      link: [{ rel: 'favicon', href: 'favicon.ico' }],
    }
  },

  data() {
    const self = this
    return {
      self,
      name: 'Kyongsik Choi',
      position: 'Senior Software Engineer',
      tel: '010-9261-1248',
      email: 'sinnerr0@gmail.com',
      linkedin:
        'http://www.linkedin.com/in/%EA%B2%BD%EC%8B%9D-%EC%B5%9C-bb108871',
      github: 'https://github.com/sinnerr0',
      workExperience: [
        {
          logo:
            'https://media-exp1.licdn.com/dms/image/C510BAQGwZYMNRPBTVg/company-logo_200_200/0?e=1600905600&v=beta&t=xI7KK91aAuo1GbRMOAQ_u673TcGTzw29WgN1LDtvta8',
          position: 'Lead Software Developer & Team Leader',
          where: 'Alchera',
          when: '2020. 04 - Present',
          role: 'Web based Application dev.',
        },
        {
          logo:
            'https://media-exp1.licdn.com/dms/image/C510BAQGwZYMNRPBTVg/company-logo_200_200/0?e=1600905600&v=beta&t=xI7KK91aAuo1GbRMOAQ_u673TcGTzw29WgN1LDtvta8',
          position: 'Lead Software Developer',
          where: 'Alchera',
          when: '2019. 04 - 2020. 03',
          role:
            'Web based Application dev.(Labeling Annotation tool for AI leaning)',
        },
        {
          logo:
            'https://media-exp1.licdn.com/dms/image/C4E0BAQFiRQxCMhQjLg/company-logo_200_200/0?e=1600905600&v=beta&t=j6S6Yv1m3auAXD-dVQ2oFKP49inKfiN_PjN0GR01bwI',
          position: 'Lead Software Developer',
          where: 'Alticast',
          when: '2017. 04 - 2019. 04',
          role: 'Web based Application dev.(Smart TV & IPTV)',
        },
        {
          logo:
            'https://media-exp1.licdn.com/dms/image/C4E0BAQFiRQxCMhQjLg/company-logo_200_200/0?e=1600905600&v=beta&t=j6S6Yv1m3auAXD-dVQ2oFKP49inKfiN_PjN0GR01bwI',
          position: 'Software Developer',
          where: 'Alticast',
          when: '2014. 06 - 2017. 03',
          role: 'Web based Application dev.(Smart TV & IPTV)',
        },
        {
          logo:
            'https://media-exp1.licdn.com/dms/image/C560BAQHaLqTJx7luBw/company-logo_200_200/0?e=1600905600&v=beta&t=7IjVcNE93fA5J5k5-C1TRz7skwBLNRYTN40tJ9pPZ3Q',
          position: 'Software Developer & Researcher',
          where: 'UXMedia Lab in Myongji university',
          when: '2009. 01 - 2013. 08',
          role: 'Research based on MPEG-V standard and Software dev.',
        },
      ],
      titles: ['PROJECTS', 'INFORMATION', 'EDUCATION', 'AWARDS'],
      projects: [
        {
          title: 'AI Service Product Develop',
          date: '2019. 06 - Present',
          contents: [
            '내용: Web Service dev',
            '담당업무: Team Leader & Frontend dev',
          ],
        },
        {
          title: 'KT Cloud 3.0 Homeportal development and maintenance 2018',
          date: '2018. 10 - 2019. 03',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: 유관부서 개선사항 적용 및 신규 서비스/기능 런칭을 위한 고도화 개발',
            '담당업무: WEB 3.0 UI dev and project leader',
            '개발인원: 6명',
          ],
        },
        {
          title: 'kt cloud homportal MTO Dynamic UI development',
          date: '2018. 10 - 2019. 03',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: 실시간 맞춤 어플리케이션 제공을 통한 마케팅 인벤토리 확대와 개인화된 맞춤 기능 추가',
            '담당업무: WEB 3.0 UI dev and project leader',
            '개발인원: 6명',
          ],
        },
        {
          title: 'KT Cloud Homeportal WEB 3.0 Migration',
          date: '2017. 04 - 2018. 10',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: WEB 3.0 UI development on the cloud stb, Management UI/DA server development for the cloud WEB 3.0 UI',
            '담당업무: WEB 3.0 UI dev and project leader',
            '개발인원: 6명',
          ],
        },
        {
          title:
            'KT olleh tv home portal Advancement - 2nd half of 2016(Cloud)',
          date: '2016. 09 - 2017. 03',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: KT홈포탈 기능 고도화 및 UI 개선 사항 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
        },
        {
          title:
            'KT_Olleh TV Cloud Web homeportal development for STB expansion',
          date: '2016. 09 - 2017. 03',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: 기종확대를 위한 Cloud Web 홈포탈 어플리케이션 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
        },
        {
          title: 'CMB LG전자 SMART TV 서비스 개발 및 솔루션 공급',
          date: '2014. 11 - 2016. 10',
          contents: [
            '발주처: (주)씨엠비홀딩스',
            '관련기술:  AngularJS 1.x, RequireJS, javascript, html, css',
            '내용: LG전자 Smart TV 2014, 2015년도 모델 Smart TV Application 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
          img: ['/cmb.JPG'],
        },
        {
          title:
            'KT olleh tv home portal Advancement - 1st half of 2016(Cloud)',
          date: '2016. 04 - 2016. 09',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: KT홈포탈 기능 고도화 및 UI 개선 사항 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
        },
        {
          title: 'KT Cloud UI',
          date: '2015. 05 - 2016. 05',
          contents: [
            '발주처: 주식회사 케이티',
            '관련기술:  javascript, Node.js',
            '내용: 커맨드 방식의 클라우드 UI 시스템 앱 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
          img: ['/kt.JPG'],
        },
        {
          title: 'CJHV LG Smart TV XCAS Porting and application dev',
          date: '2014. 07 - 2015. 12',
          contents: [
            '발주처: (주)씨제이헬로비전',
            '관련기술:  jquery, javascript, html, css',
            '내용: LG전자 Smart TV 2014, 2015년도 모델 Smart TV Application 개발',
            '담당업무: 홈포탈 dev.',
            '개발인원: 3명',
          ],
          img: [
            '/CJHV LG Smart TV XCAS Porting and application dev1.JPG',
            '/CJHV LG Smart TV XCAS Porting and application dev.JPG',
          ],
        },
        {
          title:
            'Automatic calorie calculators for outdoor exercise equipment and its health avatar app',
          date: '2012. 06 - 2013. 05',
          contents: [
            '전시: MPEG Multimedia Ecosystem 2013 Showcase',
            '관련기술: Android SDK, Java',
            '내용: 옥외 운동기구에 부착되는 가속도 센서 컨트롤 모듈 개발, 전체 아키텍쳐 설계 및 헬스아바타 앱 설계, 데이터베이스와 헬스아바타 앱간의 통신모듈 개발, MPEG-V 표준을 이용한 데이터 인디코더 개발, 옥외 운동기구를 통한 운동횟수측정 알고리즘 개발',
            '담당업무: 운동횟수측정 알고리즘 및 Client Application dev, MPEG-V 표준 인디코더 dev.',
            '개발인원: 3명',
          ],
          img: [
            '/Automatic calorie calculators for outdoor exercise equipment and its health avatar app.JPG',
          ],
        },
        {
          title: 'MPEG-V 표준 기술 응용 S/W(Facial Expression Cloning)',
          date: '2012. 12 - 2013. 05',
          contents: [
            '발주처: 삼성전자',
            '관련기술: C++, MFC',
            '내용: C로 개발된 Face Tracking Library를 이용하여 얼굴 추출 된 포인터 패키지화, MPEG-V 표준 기술에 적합한 UX/UI 개발, MPEG-V 표준에 기반한 소프트웨어 엔진 개발, CLR을 이용하여 C++로 된 MPEG-V 인디코더 MFC와 연동, MPEG-V 표준을 따르는 인디코더 개발',
            '담당업무: UX/UI 및 Client Application dev.',
            '개발인원: 1명',
          ],
          img: ['/Facial Expression Cloning.JPG'],
        },
        {
          title: '실감미디어를 위한 인간 감각 반응 및 선호도에 대한 연구',
          date: '2010. 05 - 2013. 04',
          contents: [
            '발주처: 한국연구재단',
            '관련기술: Flex, Java',
            '내용: Wireless device controller module 개발, 차량 내 실감미디어 시뮬레이션과 실감미디어 제어 시스템간 네트워크 통신 모듈 개발',
            '담당업무: 무선 장치 제어 모듈 개발, 시뮬레이션 Software와 장치 제어 모듈간 통신을 위한 네트워크 통신 모듈 개발',
            '개발인원: 2명',
          ],
          img: ['/augmented media.JPG'],
        },
        {
          title: '3D 아바타 실감 얼굴 재현 메타데이터 표준화 연구',
          date: '2012. 10 - 2013. 02',
          contents: [
            '발주처: ETRI',
            '관련기술: Java',
            '내용: 표준 메타데이터 및 바이너리 포멧을 이용한 알고리즘 및 시스템 연구 개발',
            '담당업무: MPEG-V 표준 인디코더 및 Client Application dev.',
            '개발인원: 2명',
          ],
        },
        {
          title: '감성 미디어 저작을 위한 감성정보 추출 및 감성 UX 엔진 연구',
          date: '2012. 06 - 2013. 01',
          contents: [
            '발주처: ETRI',
            '관련기술: Java',
            '내용: 사용자 선호 색감에 따른 색감 변환 알고리즘 구현, 국제 표준을 준용하는 감각효과 XML 생성 및 검증 인디코더 모듈 개발',
            '담당업무: 색감 변환 알고리즘 구현, 표준기반 인디코더 모듈 개발',
            '개발인원: 2명',
          ],
        },
        {
          title:
            'RFID/USN 기반의 지능형 U-Wellness 통합관리시스템 개발 및 구축 사업',
          date: '2011. 07 - 2012. 06',
          contents: [
            '발주처: 대양이티엔씨',
            '관련기술: Android SDK, Java',
            '내용: ISO/IEC 23005, 23007 국제 표준을 준수하는 XML 기반의 데이터 인코딩/디코딩/엔진 프레임워크 개발, 개인 맞춤형 운동 트레이너 앱 개발, USN 기반의 무산소 근력운동 횟수 및 근력운동량 측정 방법 및 알고리즘 개발, 지능형 데이터웨어하우스와 헬스 아바타 연계방법 연구',
            '담당업무: 표준 기반의 인디코딩 모듈 및 엔진 개발, 운동횟수 및 운동량 측정 알고리즘 개발',
            '개발인원: 4명',
          ],
          img: ['/RFID USN.JPG'],
        },
        {
          title: 'MPEG-V 3D 아바타 실감 재현 표준화 연구',
          date: '2012. 03 - 2012. 04',
          contents: [
            '발주처: ETRI',
            '관련기술: Java',
            '내용: 표준 메타데이터 및 바이너리 포멧을 이용한 알고리즘 및 시스템 연구 개발',
            '담당업무: 국제 표준 인디코더 개발',
            '개발인원: 2명',
          ],
        },
        {
          title: 'MPEG-V 메타데이터 및 바이너리 포멧의 국제 표준화 연구',
          date: '2011. 09 - 2012. 01',
          contents: [
            '발주처: ETRI',
            '관련기술: Java',
            '내용: 표준 메타데이터 및 바이너리 포멧을 이용한 알고리즘 및 시스템 연구 개발',
            '담당업무: 국제 표준 인디코더 개발',
            '개발인원: 2명',
          ],
        },
        {
          title: '무선센서 정보의 데이터 구조설계 및 Compact 화',
          date: '2011. 04 - 2011. 07',
          contents: [
            '발주처: 삼성전자',
            '관련기술: Java',
            '내용: 이진화 검증 단계를 포함하는 이진 표현 인코딩/디코딩 기능을 첨부한 이진화 표현(binary representation) 소프트웨어 개발',
            '담당업무: 인코딩/디코딩 이진화 표현 소프트웨어 dev.',
            '개발인원: 2명',
          ],
        },
        {
          title:
            'MPEG-V Utility 소프트웨어 개발(Adaptation Engine Utility Software)',
          date: '2010. 04 - 2010. 12',
          contents: [
            '발주처: 삼성전자',
            '관련기술: Java',
            '내용: XML과 JAXB를 이용한 컬러리프로덕션 메타데이터 표준 소프트웨어 개발, Real World의 다양한 센서(온도, 습도, 진동, 가속도, 조도 등)로부터 데이터를 수집해서 Virtual World의 다양한 가상 객체(Virtual Object)의 상태나 속성, 애니메이션과 같은 제어를 수행하는 모듈 개발',
            '담당업무: 표준 인디코더 dev.',
            '개발인원: 2명',
          ],
        },
        {
          title: 'Sensory Effect Authoring Tool',
          date: '2010. 03 - 2010. 12',
          contents: [
            '전시: MPEG-V Awareness Event 2011',
            '관련기술: Flex SDK, Java',
            '내용: 표준 XML 형태의 감각효과 메타데이터 import & export 모듈 설계 개발, 감각효과들을 직관적이고 편리하게 컨트롤 할 수 있는 타임라인 UI 설계 개발',
            '담당업무: 표준 인디코더 및 import/export 모듈 개발, 4D Sensory metadata 제어를 위한 timeline UI 설계 및 개발',
            '개발인원: 3명',
          ],
          img: ['/Sensory Effect Authoring Tool.JPG'],
        },
        {
          title: 'MPEG-V 컬러리프로덕션 표준화 연구',
          date: '2010. 04 - 2010. 06',
          contents: [
            '발주처: ETRI',
            '관련기술: Java',
            '내용: XML과 JAXB를 이용한 컬러리프로덕션 메타데이터 표준 소프트웨어(Reference SW) 개발, 이진 포멧 인코더/디코더 개발, 컬러리프로덕션 알고리즘을 통합한 컬러리프로덕션 시뮬레이션 도구 개발',
            '담당업무: 표준 인디코더 개발, 컬러리프로덕션 알고리즘 구현 및 Client Application dev.',
            '개발인원: 2명',
          ],
        },
      ],
      information: [
        {
          title: '',
          date: '',
          contents: [],
          img: [],
        },
      ],
      education: [
        {
          title: '',
          date: '',
          contents: [],
          img: [],
        },
      ],
      awards: [
        {
          title: '2010 Computer Engineering Creative Sense 학술제 우수상',
          date: '2010. 12 명지대학교컴퓨터공학과',
          contents: [],
          img: [],
        },
        {
          title: '2010 교내 캡스톤디자인 프로젝트 경진대회 금상',
          date: '2010. 12 명지대학교',
          contents: [],
          img: [],
        },
      ],
    }
  },
}
</script>
