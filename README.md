# Meme-Template-Viewer:-


Meme Template Viewer — React Project:-

This is a  project jisme React ka use karke hum internet se meme templates lekar ek gallery jaisi listing banate hain.
User search bar me naam likh kar memes ko filter bhi kar sakta hai.
Pure kaam browser side par hota hai — backend ki koi need nhoi hoti hai.

Overview of Project:-

Is app ka main idea yeh hai:

Public API se meme templates download karna

Unhe grid layout me neatly arrange karke show karna

User ko search ki madad se memes dhoondhne ka option dena


Meme Data Kahan Se Aata Hai?:-

Data fetch karne ke liye Imgflip ka free meme API use kiya gaya hai.

API URL:

https://api.imgflip.com/get_memes


API response me ek data.memes array hota hai jisme har meme ka:

name

image link

dimensions

Id

present hota hai.

Data Fetching Process:-

Jab component first time render hota hai:

useEffect() ke andar ek async request bheji jaati hai

Response milte hi meme list state me save hoti hai

Agar fetching fail ho jaaye toh error message show hota hai

Example flow:

useEffect(() => {
  async function load() {
    const res = await fetch(API_URL)
    const json = await res.json()
    setMemes(json.data.memes)
  }
  load()
}, [])


Simple aur seedha approach.

Search Kaise Kaam Karta Hai?:-

Jo meme list humne API se li hai, filtering usi par hoti hai.

Search text ko lowercase me convert kiya jata hai

Phir matching memes ko nikal kar show kiya jata hai

Isme koi extra API call nahi hoti

Example logic:

const results = useMemo(() => {
  return memes.filter(m =>
    m.name.toLowerCase().includes(search.toLowerCase())
  )
}, [search, memes])

Tools & Technologies Used:-

React — UI banane ke liye

Vite — fast development environment

Tailwind CSS — styling ke liye utility classes

 UI & Styling:-

Tailwind CSS ki classes se pura layout build kiya gaya hai

Grid system responsive hai: mobile, tablet, desktop par adjust ho jaata hai

Images ko object-cover se resize kiya gaya hai taaki cards uniform dikhe

Search bar, cards aur spacing sab Tailwind utilities se handled hain

Useful Commands:-
Command	Kaam
npm run dev	Project local host par chalata hai
npm run build	Production files generate karta hai
npm run preview	Build ka preview local machine par

Points to be noted:-

App sirf data show karta hai, koi writing/editing nahi hoti

Slow internet par loader dikhega

API down ho toh error safe handling available hai

Code lightweight hai, beginners ke liye perfect
