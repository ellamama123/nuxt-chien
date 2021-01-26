<template>
                    <form>
                        <div class="form-group">
                            <label for="exampleFormControlInput1">Tiêu đề</label>
                            <input type="text" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
                        </div>
                        <div class="form-group">
                            <label for="exampleFormControlInput1">Tiêu đề</label>
                            <input type="text" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
                        </div>
                        <div class="form-group">
                            <p for="exampleFormControlTextarea1">Example textarea</p>
                            <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                        </div>

                        <div class="form-group">
                            <p for="exampleFormControlFile1">Example file input</p>
                            <input type="file" class="form-control-file" id="exampleFormControlFile1">
                        </div>

                        <div class="form-group">
                            <p class="mr-sm-2" for="inlineFormCustomSelect">Loại</p>
                            <select class="custom-select mr-sm-2" id="inlineFormCustomSelect">
                                <option selected>Choose...</option>
                                <option value="1">One</option>
                                <option value="2">Two</option>
                                <option value="3">Three</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <p>Vị trí</p>
                            <ul class="list-group list-group-flush">
                                <li class="list-group-control">
                                    <label class="custom-control custom-radio">
                                        <input name="radio" type="checkbox" class="custom-control-input">
                                        <span class="custom-control-indicator"></span>
                                        <span class="custom-control-description">Custom radio</span>
                                    </label>
                                </li>
                                <li class="list-group-control">
                                    <label class="custom-control custom-radio">
                                        <input name="radio" type="checkbox" class="custom-control-input">
                                        <span class="custom-control-indicator"></span>
                                        <span class="custom-control-description">Custom radio</span>
                                    </label>
                                </li>
                                <li class="list-group-control">
                                    <label class="custom-control custom-radio">
                                        <input name="radio" type="checkbox" class="custom-control-input">
                                        <span class="custom-control-indicator"></span>
                                        <span class="custom-control-description">Custom radio</span>
                                    </label>
                                </li>
                            </ul>
                        </div>
                        <div class="form-group">
                            <div class="row">
                                <p>Public</p>
                                <div class="col-8">
                                    <div class="custom-control custom-radio">
                                        <input type="radio" id="customRadio1" name="customRadio" class="custom-control-input" checked>
                                        <label class="custom-control-label" for="customRadio1">Yes</label>
                                    </div>
                                    <div class="custom-control custom-radio">
                                        <input type="radio" id="customRadio2" name="customRadio" class="custom-control-input">
                                        <label class="custom-control-label" for="customRadio2">No</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="form-group row">
                            <p for="example-datetime-local-input" class="col-form-label">Date</p>
                            <div class="">
                                <input class="form-control" type="datetime-local" value="2011-08-19T13:45:00" id="example-datetime-local-input">
                            </div>
                        </div>
                        <div class="form-group">
                            <button type="button" class="btn btn-success">Submit</button>
                            <button type="button" class="btn btn-primary">Clear</button>
                        </div>

                    </form>
</template>
<script>
export default {
    
}
</script>
