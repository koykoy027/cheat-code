# REACTJS KNOWLEDGE
<details>
  <summary>fetch-in-single-components</summary>

  
  ```js
  const url = "http://127.0.0.1:8000/api/students/";
  
  const [students, setStudents] = useState([]);
  
  
  // with useEffect
  useEffect(() => {
    const fetchStudents = async () => {
      try{
        const res = await fetch(url);
        const response = await res.json();
        setStudents(response);
      }catch(error){
        console.log("Something went wrong", error);
      }
  
    }
    fetchStudents();
  
  }, []);
  
  ```

</details>

---

<details>
  <summary>fetch-via-seperate-folders</summary>

  ### create .env
  ```.env
  VITE_API_URL="http://127.0.0.1:8000/api"
  ```

### src\lib\helpers\http.ts
  ```js
  export const fetchJson = async (url: string, options?: RequestInit) => {
    try {
      const response = await fetch(url, options);
  
      if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
      }
  
      return await response.json();
    } catch (error) {
      console.error('Error fetching data:', error);
      throw error;
    }
  };
  ```

  ### src\lib\apis\students.ts
  ```js
  import { fetchJson } from '../helpers/http';
  
  const baseUrl = import.meta.env.VITE_API_URL || '';
  
  export const fetchStudents = async () => {
    const url = `${baseUrl}/students`;
    return fetchJson(url);
  };
  ```

  ### components
  ```js
  const [students, setStudents] = useState([]);
  
  useEffect(() => {
    const fetchData = async () => {
      try {
        const studentsData = await fetchStudents();
        setStudents(studentsData);
      } catch (error) {
        console.log("Something went wrong", error);
      }
    };

    fetchData();
  }, []);
  ```
  
</details>
