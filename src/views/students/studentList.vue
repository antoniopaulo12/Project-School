<template>
  <div class="card">
    <div class="d-grid gap-2 d-md-flex justify-content-md-end">
      <button type="button" class="btn btn-primary me-md-2" data-bs-toggle="modal" data-bs-target="#addModal" data-bs-whatever="@mdo">Insertar Estudiente</button>
    </div>
      <div class="modal fade" id="addModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Agregar Estudiante</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
            <div class="modal-body">
          <form>
           <div class=" input-group">
            <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Nombres:</label>
              <input v-model="postStudent.student_name" type="text" class="form-control" id="recipient-name">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Apellidos:</label>
              <input v-model="postStudent.student_lastName" type="text" class="form-control" id="recipient-name">
            </div>
          </div>
          <div class="mb-3">
              <label for="recipient-name" class="col-form-label">Direccion:</label>
              <input v-model="postStudent.student_address" type="text" class="form-control" id="recipient-name">
          </div>
          <div class="input-group mb-3">
            <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Genero:</label>
              <input v-model="postStudent.student_sex" type="text" class="form-control" id="recipient-name">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Padre:</label>
              <input v-model="postStudent.student_father" type="text" class="form-control" id="recipient-name">
            </div>
             <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Madre:</label>
              <input v-model="postStudent.student_mother" type="text" class="form-control" id="recipient-name">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Encargado:</label>
              <input v-model="postStudent.student_manager" type="text" class="form-control" id="recipient-name">
            </div>
            <div  class="me-md-4">
              <label for="recipient-name" class="col-form-label">Fecha de nacimiento:</label>
              <input v-model="postStudent.student_datebirth" class="form-control" type="date" id="example-date-input">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Fecha de registro:</label>
              <input v-model="postStudent.student_registration" class="form-control" type="date"  id="example-date-input">
            </div>
          </div>
          <div>
             <label for="recipient-name" class="col-form-label">Cursos:</label>
              <select v-model="postStudent.course_id" class="form-control">
                <option v-for="(course, index) in courses" :key="index" :value="parseInt(course.course_id)">{{ course.course_name }}</option>
              </select>
            </div>
        </form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button  @click.prevent="saveStudent" type="button" class="btn btn-primary" data-bs-dismiss="modal">Guardar</button>
      </div>
    </div>
  </div>
      </div>
      <div class="modal fade" id="editModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Editar Estudiante</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
            <div class="modal-body"  >
          <form>
           <div class=" input-group" >
            <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Nombre:</label>
              <input v-model="postStudent.student_name" class="form-control" >
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Apellidos:</label>
              <input v-model="postStudent.student_lastName" type="text" class="form-control" id="recipient-name">
            </div>
          </div>
          <div class="mb-3">
              <label for="recipient-name" class="col-form-label">Direccion:</label>
              <input v-model="postStudent.student_address" type="text" class="form-control" id="recipient-name">
          </div>
          <div class="input-group mb-3">
            <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Genero:</label>
              <input v-model="postStudent.student_sex" type="text" class="form-control" id="recipient-name">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Padre:</label>
              <input v-model="postStudent.student_father" type="text" class="form-control" id="recipient-name">
            </div>
             <div class="me-md-4">
              <label for="recipient-name" class="col-form-label">Madre:</label>
              <input v-model="postStudent.student_mother" type="text" class="form-control" id="recipient-name">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Encargado:</label>
              <input v-model="postStudent.student_manager" type="text" class="form-control" id="recipient-name">
            </div>
            <div  class="me-md-4">
              <label for="recipient-name" class="col-form-label">Fecha de nacimiento:</label>
              <input v-model="postStudent.student_datebirth" class="form-control" type="date" id="example-date-input">
            </div>
            <div>
              <label for="recipient-name" class="col-form-label">Fecha de registro:</label>
              <input v-model="postStudent.student_registration" class="form-control" type="date"  id="example-date-input">
            </div>
          </div>
          <div>
             <label for="recipient-name" class="col-form-label">Cursos:</label>
              <select v-model="postStudent.course_id" class="form-control">
                <option v-for="(course, index) in courses" :key="index" :value="parseInt(course.course_id)">{{ course.course_name }}</option>
              </select>
            </div>
        </form>
      </div>
      <div class="modal-footer">
        <button  type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cerrar</button>
        <button  @click.prevent="saveStudent" type="button" class="btn btn-primary" data-bs-dismiss="modal">Guardar</button>
      </div>
    </div>
  </div>
      </div>
    <div  class="card-body px-0 pt-0 pb-2">
      <div   class="table-responsive p-0">
        <table  class="table table-hover">
          <thead class="table-dark">
            <tr>
              <th scope="col">rne</th>
              <th scope="col">Nombre</th>
              <th scope="col">Apellido</th>
              <th scope="col">Direccion</th>
              <th scope="col">Sexo</th>
              <th scope="col">Padre</th>
              <th scope="col">Madre</th>
              <th scope="col">Encargado</th>
              <th scope="col">Fecha de Nacimiento</th>
              <th scope="col">Fecha de registro</th>
              <th scope="col"></th>
            </tr>
          </thead>
          <tbody >
            <tr v-for="student in students" :key="student.student_rne">
              <th>{{ student.student_rne }}</th>
              <td>{{ student.student_name }}</td>
              <td>{{ student.student_lastName }}</td>
              <td>{{ student.student_address }}</td>
              <td>{{ student.student_sex }}</td>
              <td>{{ student.student_father }}</td>
              <td>{{ student.student_mother }}</td>
              <td>{{ student.student_manager }}</td>
              <td>{{ student.student_datebirth }}</td>
              <td>{{ student.student_registration }}</td>
              <td>
                <div class="btmn-group" role="group" aria-label="">
                   <button  @click.prevent="getStudentById(student.student_rne)" type="button" class="btn btn-success me-md-2" data-bs-toggle="modal" data-bs-target="#editModal" data-bs-whatever="@mdo">Editar</button>
                  <button @click.prevent="deleteStudent(student.student_rne)" type="button" class="btn btn-danger">Borrar</button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "students-List",
  data(){
      return {
         students: [],
         studentsEdit: {
          "student_name": "",
          "student_lastName": "",
          "student_address": "",
          "student_sex": "M",
          "student_father": "",
          "student_mother": "",
          "student_manager": "",
          "student_registration": "",
          "student_datebirth": "",
          "course_id": ""
         },
         postStudent: {},
         courses: [],
      }
  },
  created(){
    this.getStudents()
    this.getCourses()
  },
   methods: {
    getStudents() {
      axios.get('http://localhost:3000/api/students')
      .then((response) => this.students = response.data)
    },
    getCourses() {
      axios.get('http://localhost:3000/api/courses')
      .then((response) => this.courses = response.data)
    },
    saveStudent(){
     axios.post('http://localhost:3000/api/students', this.postStudent)
     .then((response) => {
      console.log(response)
      this.getStudents()
     })
    },
    deleteStudent(student_rne){
      console.log(student_rne)
      axios.delete(`http://localhost:3000/api/students/${student_rne}`)
      .then((response) =>  {
        console.log('dato eliminado con exito',response)
       this.getStudents()
      }
    )},
    },
};

</script>
