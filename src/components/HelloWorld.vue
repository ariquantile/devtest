<template>
<div class="hello container mb-5 pb-5">
    <h1 class="bg-success text-warning text-center py-2">Home Page</h1>
    <div class="row">
        <div class="col-8 offset-2">

            <form>
                <div class="form-group">
                    <label for="exampleInputEmail1">Email address</label>
                    <input type="email" v-model.trim="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">

                </div>
                <div class="form-group">
                    <label for="exampleInputPassword1">Password</label>
                    <input type="password" v-model="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
                </div>
                <div class="form-group">
                    <label for="exampleFormControlSelect1">Example select</label>
                    <select v-model="select_dropdown" class="form-control" id="exampleFormControlSelect1">
                        <option>1</option>
                        <option>2</option>
                        <option>3</option>
                        <option>4</option>
                        <option>5</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="exampleFormControlSelect1">Create Multiple Tags</label>
                    <div class="form-group">
                        <input type="text" v-on:keyup.enter="addTag" v-model="text_tag" class="form-control" id="exampleTags" placeholder="Create Tags">
                    </div>

                </div>
                <ul>
                    <li v-for="(tag,i) in tags" :key="i" style="list-style:none;">
                        <div>
                            <h6 style=" border: .5px dotted blue;" class="mt-1">
                                <span class="mr-3">{{tag}}</span>
                                <span @click="removeTag(i)">X</span>
                            </h6>
                        </div>

                    </li>
                </ul>

                <div>

                </div>

                <div class="row justify-content-center">
                    <div class="col-6">
                        <fieldset class="form-group">
                            <div class="row">
                                <legend class="col-form-label col-sm-2 pt-0">Radios</legend>
                                <div class="col-sm-10">
                                    <div class="form-check">
                                        <input class="form-check-input" v-model="select_radio" type="radio" name="gridRadios" id="gridRadios1" value="option1" checked>
                                        <label class="form-check-label" for="gridRadios1">
                                            First radio
                                        </label>
                                    </div>
                                    <div class="form-check">
                                        <input class="form-check-input" v-model="select_radio" type="radio" name="gridRadios" id="gridRadios2" value="option2">
                                        <label class="form-check-label" for="gridRadios2">
                                            Second radio
                                        </label>
                                    </div>
                                    <div class="form-check">
                                        <input class="form-check-input" v-model="select_radio" type="radio" name="gridRadios" id="gridRadios3" value="option3">
                                        <label class="form-check-label" for="gridRadios3">
                                            Third disabled radio
                                        </label>
                                    </div>
                                </div>
                            </div>
                        </fieldset>
                    </div>

                    <div class="col-6">
                        <div class="form-check">
                            <input type="checkbox" value="One" v-model="select_check_box" class="form-check-input" id="exampleCheck1">
                            <label class="form-check-label" for="exampleCheck1">One</label>

                        </div>

                        <div class="form-check">
                            <input type="checkbox" value="Two" class="form-check-input" v-model="select_check_box" id="exampleCheck2">
                            <label class="form-check-label" for="exampleCheck2">Two</label>
                        </div>

                        <div class="form-check">
                            <input type="checkbox" value="Three" class="form-check-input" v-model="select_check_box" id="exampleCheck3">
                            <label class="form-check-label" for="exampleCheck3">Three</label>

                        </div>

                    </div>
                </div>
                <button type="submit" @click.prevent="AddValue" class="btn btn-primary mt-5">Submit</button>
            </form>

        </div>

    </div>

    <div class="mt-4">
        <p class="text-center text-info">submitted Values:</p>
        <div v-if="is_submit">
            Email:{{email}} <br>
            Password:{{password}} <br>
            Dropdown:{{select_dropdown}} <br>
            Radio:{{select_radio}} <br>
            CheckBox:{{select_check_box}} <br>
            Tags:{{tags}}

        </div>

    </div>

    <div class="mt-5">
        <p class="text-center text-danger bg-warning">New From</p>

    </div>

</div>
</template>

<script>
export default {
    data() {
        return {
            email: "",
            password: "",
            select_dropdown: "",
            select_radio: "",
            select_check_box: [],
            is_submit: false,
            text_tag: "",
            tags: [],
            testList: []

        }
    },

    methods: {
        AddValue() {
            this.is_submit = true
            document.getElementById("exampleInputEmail1").value = "Johnny Bravo@gmail.com";

        },
        addTag() {
            this.tags.push(this.text_tag)

            var myListofArrays = [];
            for (var i = 1; i <= 1; i++) {
                myListofArrays.push([i, this.tags])
            }
            console.log(myListofArrays)

            this.text_tag = ""

        },
        removeTag(index) {
            this.tags.splice(index, 1)

        }

    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>

</style>
